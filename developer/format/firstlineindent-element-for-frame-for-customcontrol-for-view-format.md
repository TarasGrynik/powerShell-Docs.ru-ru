---
title: Элемент FirstLineIndent для кадра для пользовательский элемент управления для представления (формат) | Документация Майкрософт
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bb4e1564-3fd3-4be3-b93e-ac90480e05c0
caps.latest.revision: 6
ms.openlocfilehash: 3130ecc69f7d1568bcbd392dd24e8cdcc3382905
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065875"
---
# <a name="firstlineindent-element-for-frame-for-customcontrol-for-view-format"></a>Элемент FirstLineIndent для элемента Frame для элемента CustomControl для элемента View (формат)

Указывает количество символов, первая строка данных сдвигается вправо. Этот элемент используется при определении представления пользовательского элемента управления.

Элемент (формат) элемент ViewDefinitions (формат) представление элемент (формат) элемент пользовательский элемент управления (формат) CustomEntries элемент конфигурации для пользовательский элемент управления для элемента представления (формат) CustomEntry для CustomEntries для элемента CustomItem представление (формат) CustomEntry CustomControlView (формат) элемента фрейма для CustomItem для пользовательский элемент управления для элемента FirstLineIndent представления (формат)

## <a name="syntax"></a>Синтаксис

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a>Атрибуты и элементы

Ниже описаны атрибуты, дочерние элементы и родительский элемент `FirstLineIndent` элемент.

### <a name="attributes"></a>Атрибуты

Нет.

### <a name="child-elements"></a>Дочерние элементы

Нет.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[Элемент Frame для CustomItem для пользовательский элемент управления для представления (формат)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|Определяет способ отображения данных, таких как данные сдвига влево или вправо.|

## <a name="text-value"></a>Текстовое значение

Укажите количество символов, которые нужно сместить первая строка данных.

## <a name="remarks"></a>Замечания

Если этот элемент указан, нельзя указать [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) элемент.

## <a name="see-also"></a>См. также

[Элемент FirstLineHanging для кадра для пользовательский элемент управления для представления (формат)](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[Элемент Frame для CustomItem для пользовательский элемент управления для представления (формат)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[Запись файла форматирования PowerShell](./writing-a-powershell-formatting-file.md)
