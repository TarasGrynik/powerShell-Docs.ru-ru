---
title: Написание справки для командлетов PowerShell | Документация Майкрософт
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55908d67-7cbe-482a-a105-5a6da93c5311
caps.latest.revision: 4
ms.openlocfilehash: 8d692cf88d1d356886ef973f0989294d6b51ee6d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083167"
---
# <a name="writing-help-for-powershell-cmdlets"></a>Написание справки для командлетов PowerShell

Командлеты PowerShell может быть полезно, но если собственных разделов справки понятно объяснить, что делает командлет и способы ее использования, командлет может не использоваться, или, что еще хуже, он может разочаровать пользователей.
Формат файла справки командлета на основе XML улучшает согласованность, но отличный справочный требуется гораздо больше.

Если вы никогда не написали справки по командлетам, ознакомьтесь со следующими указаниями.
XML-схемы, необходимые для создания раздела справки командлета описан в следующем разделе.
Начните с [Создание файла справки по командлетам](./how-to-create-the-cmdlet-help-file.md).
Этот раздел содержит описание верхнего уровня XML-узлов.

## <a name="writing-guidelines-for-cmdlet-help"></a>Записи, касающиеся справки по командлетам

### <a name="write-well"></a>Также запись
Ничего не заменяет правильно составленный раздела.
Если вы не составителем professional, найти модуль записи или редактор, которые помогут вам.
Другой вариант — скопировать текст справки в Microsoft Word и использовании грамматики и орфографии проверяет, чтобы улучшить работу.

### <a name="write-simply"></a>Просто написать
Используйте простые слова и фразы.
Избегайте жаргон.
Рассмотрим, что многие читатели обладают только с помощью внешнего словаря и справки.

### <a name="write-consistently"></a>Постоянно записи
Справка для связанных с ним командлетов должно быть аналогично (для, например, get-x и set-x).
Используйте стандартные описания для стандартных параметров, например **Force** и **InputObject**.
(Скопировать их из справки по основным командлетам.) Используйте стандартные условия.
Например, используйте «параметр», не «аргумент», и используйте «командлет» не «команду» или «команда let».

### <a name="start-the-synopsis-with-a-verb"></a>Запустить развернутое с помощью команды
Поле краткий обзор пользователю не какой командлет, что это такое и как это работает.
Команды Создать инструкцию на основе задач, которая информирует пользователей, если этот командлет соответствует их требованиям.
Используйте простые команды, например «get», «создать» и «изменить».
Избегайте «set», который может быть неопределенным и она же, такие как «изменить».

### <a name="focus-on-objects"></a>Сосредоточиться на объекты
Большинство «get» отображение командлетов что-нибудь, но является их основной функцией для получения объекта.
В помощь рассмотрим объект, чтобы было понятно, что по умолчанию отображается одним из многих, и они могут использовать методы и свойства объекта, который вы получили для них по-разному.

### <a name="write-detailed-descriptions"></a>Подробные описания
Кратко перечислены все, что командлет можно делать в подробном описании.
Если основной функцией является изменение одного свойства, но командлет можно изменить все свойства, список это в подробном описании.

### <a name="use-conventional-syntax"></a>Используйте обычные синтаксис
Используйте стандартный формат форма Бэкуса-Наура, которые являются общими для Windows и UNIX Справка по командной строке.

### <a name="use-microsoft-net-framework-types-for-parameter-values"></a>Использование типов Microsoft .NET Framework для значений параметра
Заполнители для значений параметров (в описании синтаксиса и параметром) показаны типы .NET Framework объектов, которые будет принимать параметр.
Группа разработчиков PowerShell разработаны это соглашение, помогающие обучить пользователей работе с .NET Framework.

### <a name="write-complete-parameter-descriptions"></a>Описание параметров завершения записи
Описания параметров необходимо проинформировать пользователей о две вещи: какой параметр не (влияние) и их необходимо ввести для значения параметров.

### <a name="write-practical-examples"></a>Запись практические примеры
Примеры должны показано, как использовать все параметры, но самое главное — Показать, как использовать командлет в реальных задач.
Начать с простого примера и написать все более сложные примеры.
В последнем примере показано, как использовать командлет в конвейере.

### <a name="use-the-notes-field"></a>Использовать поле «заметки»
Используйте поле примечания для объяснения концепции, что пользователи должны знать командлет.
Заметки также можно использовать, чтобы помочь пользователям избежать распространенных ошибок.
Избегайте URL-адреса, как их изменения.
Вместо этого предоставляют пользователям термины для поиска.

### <a name="test-your-help"></a>Тестирование помощь
Тестирование окна справки, так же, как тестировать код.
Иметь друзей и коллег чтение содержимого справки и отправки отзывов.
Можно также запросить отзывы от участников групп новостей.

## <a name="see-also"></a>См. также

 [Создание файла справки по командлетам](./how-to-create-the-cmdlet-help-file.md)

 [Как добавить имя командлета и краткий обзор раздела справки по командлету](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [Как добавить подробное описание раздела справки по командлету](./how-to-add-a-cmdlet-description.md)

 [Как добавить синтаксис для раздела справки по командлету](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [Как добавить параметры для раздела справки по командлету](./how-to-add-parameter-information.md)

 [Как добавлять типы входных данных для раздела справки командлета](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [Как добавить возвращаемые значения для раздела справки по командлету](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [Добавление заметки для раздела справки по командлету](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [Как добавить примеры для раздела справки по командлету](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [Добавление ссылки по теме раздела справки по командлету](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [Пакет SDK для Windows PowerShell](../windows-powershell-reference.md)