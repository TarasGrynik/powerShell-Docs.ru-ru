---
title: Имя типа элемента для типов (формат) | Документация Майкрософт
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0595b99e-b438-4240-b47b-555cf0316f33
caps.latest.revision: 15
ms.openlocfilehash: bd5baa03c2050b2c3bbe1d7697c253d923175d39
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083796"
---
# <a name="typename-element-for-types-format"></a>Элемент TypeName для элемента Types (формат)

Указывает тип объекта, который принадлежит к набору выбора .NET.

SelectionSet элемент SelectionSets (формат) элемент (формат) для конфигурации элемента (формат) типы элемента (формат) элемент TypeName типов (формат)

## <a name="syntax"></a>Синтаксис

```xml
<TypeName>Nameof.NetType</Name>
```

## <a name="attributes-and-elements"></a>Атрибуты и элементы

В следующих разделах атрибуты, дочерние элементы и родительский элемент `TypeName` элемент. По крайней мере один `TypeName` элемент должен быть включен в наборе выбора.

### <a name="attributes"></a>Атрибуты

Нет.

### <a name="child-elements"></a>Дочерние элементы

Нет.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[Типы элемента (формат)](./types-element-for-selectionset-format.md)|Определяет объекты .NET, заданных в выделении.|

## <a name="text-value"></a>Текстовое значение

Укажите полное имя типа .NET.

## <a name="remarks"></a>Замечания

Выбор наборов можно использовать при наличии набора связанных объектов, которые вы хотите ссылаться, используя одно имя, таких как набор объектов, которые связаны через наследование. При определении представления, можно указать набор объектов, используя имя выбора вместо перечисления всех объектов в каждом представлении.

Общие наборы выбора указываются по имени, при определении представлений для форматирования файла. В этих случаях `SelectionSetName` дочерний элемент элемента `ViewSelectedBy` элемент для представления задает набор. Тем не менее различные записи представления можно также указать набора, который применяется к только что операции представления. Дополнительные сведения о наборах выделения, см. в разделе [определение задает объектов](./defining-selection-sets.md).

## <a name="example"></a>Пример

В следующем примере показан `SelectionSet` элемент, который определяет четыре типа .NET.

```
<SelectionSets>
  <SelectionSet>
    <Name>FileSystemTypes</Name>
    <Types>
     <TypeName>System.IO.DirectoryInfo</TypeName>
     <TypeName>System.IO.FileInfo</TypeName>
     <TypeName>Deserialized.System.IO.DirectoryInfo</TypeName>
     <TypeName>Deserialized.System.IO.FileInfo</TypeName>
    </Types>
  </SelectionSet>
</SelectionSets>
```

## <a name="see-also"></a>См. также

[Определение наборов Выбор](./defining-selection-sets.md)

[Элемент SelectionSet (формат)](./selectionset-element-format.md)

[Элемент SelectionSets (формат)](./selectionsets-element-format.md)

[Типы элемента (формат)](./types-element-for-selectionset-format.md)

[Запись файла форматирования Windows PowerShell](./writing-a-powershell-formatting-file.md)
