---
title: Элемент CustomEntries для пользовательский элемент управления для элементов управления для представления (формат) | Документация Майкрософт
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3485958a-ba87-4932-907c-a8f140c4abdb
caps.latest.revision: 8
ms.openlocfilehash: 4856aee930285781a101868bd6cb67824585bce1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066589"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-view-format"></a>Элемент CustomEntries для элемента CustomControl для элемента Controls для элемента View (формат)

Предоставляет определения для элемента управления. Этот элемент используется при определении элементов управления, которые могут использоваться представлением.

Конфигурации элемента (формат) элемент ViewDefinitions (формат) представление элемента (формат) элементы управления элемента (формат) элемент управления для элементов управления для элемента представления (формат) пользовательский элемент управления для элемента управления для элементов управления для элемента CustomEntries представления (формат) для Пользовательский элемент управления для элементов управления для представления (формат)

## <a name="syntax"></a>Синтаксис

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>Атрибуты и элементы

В следующих разделах атрибуты, дочерние и родительские элементы из `CustomEntries` элемент. Не ограничено максимальное число дочерних элементов, которые могут быть указаны.

### <a name="attributes"></a>Атрибуты

Нет.

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание|
|-------------|-----------------|
|[Элемент CustomEntry для CustomEntries для элементов управления для представления (формат)](./customentry-element-for-customentries-for-controls-for-view-format.md)|Обязательный элемент.<br /><br /> Предоставляет определение элемента управления.|

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[Пользовательский элемент управления элемент для элемента управления для элементов управления для представления (формат)](./customcontrol-element-for-control-for-controls-for-view-format.md)|Определяет элемент управления, используемый представлением.|

## <a name="remarks"></a>Замечания

В большинстве случаев элемент управления имеет только одно определение, которое указано в одном `CustomEntry` элемент. Тем не менее можно указать несколько определений, если вы хотите использовать тот же элемент управления для отображения различных объектов .NET. В таких случаях можно определить `CustomEntry` элемент для каждого объекта или набора объектов.

## <a name="see-also"></a>См. также

[Элемент CustomEntry для CustomEntries для элементов управления для представления (формат)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[Пользовательский элемент управления элемент для элемента управления для элементов управления для представления (формат)](./customcontrol-element-for-control-for-controls-for-view-format.md)

[Запись файла форматирования PowerShell](./writing-a-powershell-formatting-file.md)
