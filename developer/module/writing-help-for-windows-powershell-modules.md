---
title: Написание справки для модулей Windows PowerShell | Документация Майкрософт
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2b58fa5-01bc-426c-a043-5c700d6578e9
caps.latest.revision: 16
ms.openlocfilehash: 443bf5f693d2ab161668de25a1097347826cb5c2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082042"
---
# <a name="writing-help-for-windows-powershell-modules"></a>Написание справки для модулей Windows PowerShell

Модули Windows PowerShell может включать разделы справки о модуле, а также о элементы модуля, такие как командлеты, поставщики, функции и сценарии. `Get-Help` Командлет отображает раздел справки для модуля в том же формате, он отображает справку для других элементов Windows PowerShell, а пользователям использовать стандарт `Get-Help` команды, чтобы получить разделы справки.

В этом документе объясняется, формат и правильное размещение разделы справки для модуля, и предлагает рекомендации для содержимого справки для модуля.

## <a name="types-of-module-help"></a>Типы модуля

Модуль может включать следующие типы справки.

- **Справку по командлетам**. Разделы справки с описанием командлетов в модуле, что XML-файлов, используйте команду помогут схемы

- **Справку по поставщикам**. Разделы справки, которые описывают поставщики в модуле — это XML-файлов, использующих поставщик справки схемы.

- **Функциям**. Разделы справки, которые описывают функции в модуле может быть, что XML-файлов, используйте команду помогут схемы или основанной на комментариях разделы справки, функции или скрипта или модуля сценария

- **Сценариям**. Разделы справки, которые описывают скрипты в модуле может быть XML-файлов, используйте команду справки схемы или разделы справки на основе комментариев в скрипте или модуль сценария.

- **(«О программе») справки**. Можно использовать общие («about») раздела справки для описания модуля и его членах и объяснить, как члены могут использоваться совместно для выполнения задач. Разделы справки — это текстовые файлы в кодировке Юникод (UTF-8). Имя файла необходимо использовать `about_<name>.help.txt` формат, например about_MyModule.help.txt. По умолчанию Windows PowerShell содержит более чем 100 этих концептуальных разделов справки, и они форматируются как в следующем примере.

  ```
  TOPIC
      about_<subject or module name>

  SHORT DESCRIPTION
      A short, one-line description of the topic contents.

  LONG DESCRIPTION
      A detailed, full description of the subject or purpose of the module.

  EXAMPLES
      Examples of how to use the module or how the subject feature works in practice.

  KEYWORDS
      Terms or titles on which you might expect your users to search for the information in this topic.

  SEE ALSO
      Text-only references for further reading. Hyperlinks cannot work in the Windows PowerShell console.

  ```

## <a name="placement-of-module-help"></a>Размещение Справка по модулям

`Get-Help` Командлет ищет файлы разделов справки модуля в языку каталога модуля.

Например на следующей схеме структура каталогов показывает расположение разделов справки по модулю SampleModule.

```
<ModulePath>
         \SampleModule
               \<en-US>
                     \about_SampleModule.help.txt
                     \SampleModule.dll-help.xml
                     \SampleNestedModule.dll-help.xml
               \<fr-FR>
                     \about_SampleModule.help.txt
                     \SampleModule.dll-help.xml
                     \SampleNestedModule.dll-help.xml

```

> [!NOTE]
> В примере  *\<ModulePath >* заполнитель представляет один из путей в `PSModulePath` переменной среды, например $home\Documents\Modules, $pshome\Modules или пользовательского пути, задаваемый пользователем.

## <a name="getting-module-help"></a>Получение справки для модуля

Когда пользователь импортирует модуль в сеанс, разделы справки для этого модуля, импортируются в сеанс вместе с модулем. Вы можете получить список файлов справки в значении ключа FileList в манифесте модуля, но разделы справки, не подвержены `Export-ModuleMember` командлета.

Вы можете предоставить модуль разделы справки на разных языках. `Get-Help` Командлет автоматически отображает разделы справки для модуля на языке, который указан для текущего пользователя в «язык и региональные стандарты» панели управления. В Windows Vista и более поздних версиях Windows `Get-Help` поиск разделов справки в языку каталога модуля в соответствии со стандартами резервный язык, установленным для Windows.

Начиная с Windows PowerShell 3.0, под управлением `Get-Help` запускает команду, командлет или функцию, автоматический импорт модуля. `Get-Help` Командлет сразу отображает содержимое разделов справки в модуле.

Если модуль содержит разделы справки, а не разделы справки по командам модуля на компьютере пользователя, `Get-Help` выводит автоматически созданную справку. Автоматически собранную справку входит синтаксис команды, параметры и типы входных и выходных данных, но не включает все описания. Текст, который предлагает пользователю попробуйте использовать содержит автоматически созданную справку `Update-Help` командлет, чтобы загрузить справку по командам из Интернета или общей папки. Также рекомендуется с помощью **Online** параметр `Get-Help` для получения Интернет-версию раздела справки.

## <a name="supporting-updatable-help"></a>Поддержка обновляемой справки

Пользователи Windows PowerShell 3.0 и более поздних версиях Windows PowerShell можно загрузить и установить обновленные файлы справки для модуля из Интернета или из локальной общей папки. `Update-Help` И `Save-Help` командлеты скрыть сведения управления от пользователя. Пользователей, работающих с `Update-Help` командлет, а затем использовать `Get-Help` командлет, чтобы читать последние файлы справки для модуля в командной строке Windows PowerShell. Пользователям не обязательно должны перезапускать Windows или Windows PowerShell.

Пользователи за брандмауэрами и без доступа к Интернету можно использовать обновляемую справку, а также. Администраторы с Интернетом, доступ к используйте `Save-Help` командлет, чтобы загрузить и установить новейшие файлы справки для общей папки. Затем с помощью пользователей **путь** параметр `Update-Help` командлет, чтобы получить последние файлы справки из общей папки.

Авторы модулей могут входят файлы справки в модуле и использовать обновляемую справку, обновления файлов справки, или пропустить файлы справки из модуля и использовать обновляемую справку для установки и для их обновления.

Дополнительные сведения об обновляемой справке см. в разделе [поддержка обновляемой справки](./supporting-updatable-help.md).

## <a name="supporting-online-help"></a>Поддержка справки в Интернете

Пользователей, которые нельзя или не устанавливайте обновления помогают на своих компьютерах файлы часто полагаются на Интернет-версию разделов справки для модуля. **Online** параметр `Get-Help` командлет открывает Интернет-версию командлет или дополнительную функцию раздел справки для пользователя в своих веб-браузере по умолчанию.

`Get-Help` Командлет использует значение **HelpUri** свойства командлета или функции, чтобы найти Интернет-версию раздела справки.

Начиная с Windows PowerShell 3.0, вы можете помочь пользователям найти Интернет-версию разделов справки для командлетов и функций, определив атрибута HelpUri в классе командлета или **HelpUri** свойство **CmdletBinding** атрибута. Значение атрибута является значение **HelpUri** свойства командлета или функции.

Дополнительные сведения см. в разделе [поддержка справки в Интернете](./supporting-online-help.md).

## <a name="see-also"></a>См. также

[Написание модуля Windows PowerShell](./writing-a-windows-powershell-module.md)

[Поддержка обновляемой справки](./supporting-updatable-help.md)

[Поддержке справки в Интернете](./supporting-online-help.md)