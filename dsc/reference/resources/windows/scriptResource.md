---
ms.date: 08/24/2018
keywords: dsc,powershell,конфигурация,установка
title: Ресурс Script в DSC
ms.openlocfilehash: 4eee5625add4d96ade7ababf7f534f597a26712d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076996"
---
# <a name="dsc-script-resource"></a>Ресурс Script в DSC

> Область применения. Windows PowerShell 4.0, Windows PowerShell 5.x

Ресурс **Script** в DSC Windows PowerShell предоставляет механизм запуска блоков сценариев на целевых узлах. Ресурс **Script** имеет свойства `GetScript`, `SetScript` и `TestScript`, которые содержат блоки скрипта, определяемые вами для выполнения соответствующих операций DSC.

## <a name="syntax"></a>Синтаксис

```
Script [string] #ResourceName
{
    GetScript = [string]
    SetScript = [string]
    TestScript = [string]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
}
```

> [!NOTE]
> Блоки `GetScript`, `TestScript` и `SetScript` хранятся в виде строк.

## <a name="properties"></a>Свойства

|Свойство|Описание|
|--------|-----------|
|GetScript|Блок скрипта, который возвращает текущее состояние узла.|
|SetScript|Блок скрипта, который DSC использует для обеспечения совместимости, если узел не находится в нужном состоянии.|
|TestScript|Блок скрипта, который определяет, находится ли узел в нужном состоянии.|
|Учетные данные| Указывает учетные данные, используемые для запуска этого сценария, если они необходимы.|
|DependsOn| Указывает, что перед настройкой этого ресурса необходимо запустить настройку другого ресурса. Например, если идентификатор первого запускаемого блока сценария для конфигурации ресурса — **ResourceName**, а его тип — **ResourceType**, то синтаксис использования этого свойства таков: `DependsOn = "[ResourceType]ResourceName"`.

### <a name="getscript"></a>GetScript

DSC не использует выходные данные `GetScript`. Командлет [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) выполняет `GetScript`, чтобы получить сведения о текущем состоянии узла. `GetScript` может не возвращать значение. Если вы указываете возвращаемое значение, используйте `hashtable` с ключом **Result** со значением `String`.

### <a name="testscript"></a>TestScript

`TestScript` выполняется DSC, чтобы определить, необходим ли запуск `SetScript`. Если `TestScript` возвращает `$false`, DSC выполняет `SetScript`, чтобы вернуть узел в нужное состояние. Этот блок скрипта должен возвращать значение `boolean`. Значение `$true` указывает, что узел совместим и `SetScript` запускать не нужно.

Командлет [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) выполняет `TestScript`, чтобы получить сведения о совместимости узлов с ресурсами **Script**. Но в этом случае `SetScript` не будет запущен независимо от того, какое значение возвращает блок `TestScript`.

> [!NOTE]
> Все выходные данные `TestScript` являются частью его возвращаемого значения. PowerShell интерпретирует нескрытые выходные данные как ненулевое значение, поэтому `TestScript` вернет `$true` независимо от состояния узла.
> Это приводит к непредсказуемым результатам, ложноположительным значениям и сложностям при устранении неполадок.

### <a name="setscript"></a>SetScript

`SetScript` изменяет узел, задавая ему требуемое состояние. Он вызывается DSC, если блок `TestScript` возвращает значение `$false`. `SetScript` не имеет возвращаемого значения.

## <a name="examples"></a>Примеры

### <a name="example-1-write-sample-text-using-a-script-resource"></a>Пример 1: написание примера текста с помощью ресурса Script

Этот пример проверяет наличие `C:\TempFolder\TestFile.txt` на каждом узле. Если такой файл не существует, он создается с помощью `SetScript`. `GetScript` возвращает содержимое файла, а его возвращаемое значение не используется.

```powershell
Configuration ScriptTest
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script ScriptExample
        {
            SetScript = {
                $sw = New-Object System.IO.StreamWriter("C:\TempFolder\TestFile.txt")
                $sw.WriteLine("Some sample string")
                $sw.Close()
            }
            TestScript = { Test-Path "C:\TempFolder\TestFile.txt" }
            GetScript = { @{ Result = (Get-Content C:\TempFolder\TestFile.txt) } }
        }
    }
}
```

### <a name="example-2-compare-version-information-using-a-script-resource"></a>Пример 2. Сравнение сведений о версии с помощью ресурса Script

В этом примере из текстового файла на исходном компьютере извлекаются сведения о *соответствующей* версии, которые сохраняются в переменной `$version`. При создании MOF-файла узла DSC заменяет переменные `$using:version` в каждом блоке сценария значением переменной `$version`. Во время выполнения сведения о *соответствующей* версии сохраняются в текстовом файле на каждом узле. При последующих выполнениях эти сведения сравниваются и обновляются.

```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script UpdateConfigurationVersion
        {
            GetScript = {
                $currentVersion = Get-Content (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
                return @{ 'Result' = "$currentVersion" }
            }
            TestScript = {
                # Create and invoke a scriptblock using the $GetScript automatic variable, which contains a string representation of the GetScript.
                $state = [scriptblock]::Create($GetScript).Invoke()

                if( $state['Result'] -eq $using:version )
                {
                    Write-Verbose -Message ('{0} -eq {1}' -f $state['Result'],$using:version)
                    return $true
                }
                Write-Verbose -Message ('Version up-to-date: {0}' -f $using:version)
                return $false
            }
            SetScript = {
                $using:version | Set-Content -Path (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
            }
        }
    }
}
```
