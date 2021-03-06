---
title: Наборы параметров командлета | Документация Майкрософт
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f902fd4d-8f6e-4ef1-b07f-59983039a0d1
caps.latest.revision: 10
ms.openlocfilehash: a5822ef1ed3c9efb5957c20255783d515de8957a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068520"
---
# <a name="cmdlet-parameter-sets"></a>Наборы параметров командлета

Windows PowerShell использует наборы параметров для позволяют использовать один командлет, который может выполнять различные действия для различных сценариев. Наборы параметров позволяют предоставлять различные параметры для пользователя и возвращают различные сведения, в зависимости от параметров, указанных пользователем.

## <a name="examples-of-parameter-sets"></a>Примеры наборов параметров

Например `Get-EventLog` командлет (предоставляемое Windows PowerShell) возвращает разную информацию в зависимости от того, является ли пользователь указывает `List` или `LogName` параметра. Если `List` параметр указан, командлет возвращает сведения о файлах журналов, сами, но не о событиях, они содержат. Если `LogName` параметр указан, командлет возвращает информацию о событиях в журнал событий. `List` И `LogName` параметры определяют две различные наборы параметров.

## <a name="unique-parameter"></a>Параметр UNIQUE командлета

Каждый набор параметров должен иметь уникальный параметр, среда выполнения Windows PowerShell можно использовать для предоставления набор соответствующих параметров. Если это возможно уникальный параметр должен быть обязательным параметром. Когда параметр является обязательным, пользователь вынужден укажите параметр и среды выполнения Windows PowerShell с помощью этого параметра для определения параметров, настроенный для использования. Уникальный параметр не может быть обязательным в том случае, если командлет должен выполняться без параметров.

## <a name="multiple-parameter-sets"></a>Несколько наборов параметров

На следующем рисунке в левом столбце отображаются три набора допустимых параметров. Параметр типа является уникальным для первого набора параметров, параметр B является уникальным для второй набор параметров, и параметр C является уникальным для третий набор параметров. Тем не менее в столбце справа от наборов параметров нет уникальный параметр.

![ps_parametersets](../media/ps-parametersets.gif)

## <a name="parameter-set-requirements"></a>Требования к параметру Set.

Следующие требования применяются для всех наборов параметров.

- Каждый набор параметров должен иметь по крайней мере один уникальный параметр. По возможности сделайте этот параметр обязательным параметром.

- Набор параметров, содержащий несколько позиционные параметры необходимо определить уникальное позиции для каждого параметра. Без два позиционных параметров можно указать ту же позицию.

- Можно объявить только один параметр в наборе `ValueFromPipeline` ключевое слово со значением `true`. Можно определить несколько параметров `ValueFromPipelineByPropertyName` ключевое слово со значением `true`.

- Если не задан параметр не указан для параметра, для всех наборов параметров относится параметр.

## <a name="default-parameter-sets"></a>Наборы параметров по умолчанию

Если определены несколько наборов параметров, можно использовать `DefaultParameterSetName` ключевое слово атрибута командлет, чтобы указать набор параметров по умолчанию. Windows PowerShell использует параметр по умолчанию, если он не может определить параметр, настроенный для использования на основе данных командой. Дополнительные сведения об атрибуте командлета см. в разделе [объявление атрибута командлет](./cmdlet-attribute-declaration.md).

## <a name="declaring-parameter-sets"></a>Объявление наборов параметров

Чтобы создать набор параметров, необходимо указать `ParameterSetName` ключевое слово при объявлении атрибут параметра для каждого параметра в наборе параметров. Для параметров, которые принадлежат несколько наборов параметров добавьте атрибут параметра для каждого набора параметров. Это позволяет определить параметр по-разному для каждого набора параметров. Например можно определить параметр как обязательные в одном наборе и необязательные в другом. Тем не менее каждый набор параметров должен содержать один уникальный параметр.

В следующем примере `UserName` параметр — это уникальный параметр Test01 набор параметров и `ComputerName` параметр — это уникальный параметр Test02 набор параметров. `SharedParam` Параметр принадлежит к обоим наборам и является обязательным для параметра Test01 установить, но необязательно для Test02 набор параметров.

```csharp
[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;

[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test02")]
public string ComputerName
{
  get { return computerName; }
  set { computerName = value; }
}
private string computerName;

[Parameter(Mandatory= true, ParameterSetName = "Test01")]
[Parameter(ParameterSetName = "Test02")]
public string SharedParam
{
    get { return sharedParam; }
    set { sharedParam = value; }
}
private string sharedParam;    [Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```