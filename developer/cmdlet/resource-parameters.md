---
title: Параметры ресурсов | Документация Майкрософт
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 460c43aa-f5c5-4a1a-a6f2-5e07db143de1
caps.latest.revision: 5
ms.openlocfilehash: 9752570e5c997ef4da56a08df14f39b77ba37a4a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067456"
---
# <a name="resource-parameters"></a>Параметры ресурсов

Ниже перечислены рекомендуемые имена и функции для параметров ресурсов. Для этих параметров ресурсов может быть сборка, содержащая класс командлета или ведущее приложение, на котором выполняется командлет.

|Параметр|Функции|
|---|---|
|**Приложения**<br>Тип данных: Строка|Реализуйте этот параметр, чтобы пользователь может указать приложение.|
|**Сборки**<br>Тип данных: Строка|Реализуйте этот параметр, благодаря которому пользователь может указать сборку.|
|**Атрибут**<br>Тип данных: Строка|Реализуйте этот параметр, благодаря которому пользователь может указать атрибут.|
|**Класс**<br>Тип данных: Строка|Реализуйте этот параметр, благодаря которому пользователь может указать класс Microsoft .NET Framework.|
|**Кластера**<br>Тип данных: Строка|Реализуйте этот параметр, благодаря которому пользователь может указать кластер.|
|**Язык и региональные параметры**<br>Тип данных: Строка|Реализуйте этот параметр, чтобы пользователь может указать язык и региональные параметры, в котором должен быть запущен командлет.|
|**Домен**<br>Тип данных: Строка|Реализуйте этот параметр, благодаря которому пользователь может указать имя домена.|
|**Диск**<br>Тип данных: Строка|Реализуйте этот параметр, благодаря которому пользователь может указать имя диска.|
|**Событие**<br>Тип данных: Строка|Реализуйте этот параметр, благодаря которому пользователь может указать имя события.|
|**Интерфейс**<br>Тип данных: Строка|Реализуйте этот параметр, чтобы пользователь может указать имя сетевого интерфейса.|
|**IP-адрес**<br>Тип данных: Строка|Реализуйте этот параметр, таким образом, пользователь может указать IP-адресом.|
|**Задание**<br>Тип данных: Строка|Реализуйте этот параметр, благодаря которому пользователь может указать задания.|
|**LiteralPath**<br>Тип данных: Строка|Реализуйте этот параметр, чтобы пользователь может указать путь к ресурсу, когда подстановочные знаки не поддерживаются. (Используйте **путь** параметр, когда поддерживаются подстановочные знаки.)|
|**Mac**<br>Тип данных: Строка|Реализуйте этот параметр, благодаря которому пользователь может указать контроллер (MAC) адреса.|
|**parentId**<br>Тип данных: Строка|Реализуйте этот параметр, чтобы пользователь может указать идентификатор родительского.|
|**путь**<br>Тип данных: String, String]|Реализуйте этот параметр, чтобы пользователь может указать пути к ресурсу, когда поддерживаются подстановочные знаки. (Используйте **LiteralPath** параметр при подстановочные знаки не поддерживаются.) Мы рекомендуем разрабатывать этот параметр так, чтобы обеспечить полную `provider:path` синтаксис, используемый поставщиками. Мы также рекомендуем разрабатывать таким образом, чтобы она работает с столько поставщиков максимально.|
|**Порт**<br>Тип данных: Целое число, строка|Реализуйте этот параметр, чтобы пользователь может указать целочисленное значение для работы в сети или строковое значение, например «biztalk» для других типов порта.|
|**Принтер**<br>Тип данных: Целое число, строка|Реализуйте этот параметр, таким образом, пользователь может указать принтер для использования командлета.|
|**Размер**<br>Тип данных: Int32|Реализуйте этот параметр, таким образом, пользователь может указать размер.|
|**TID**<br>Тип данных: Строка|Реализуйте этот параметр, благодаря которому пользователь может указать идентификатор транзакции (TID) для командлета.|
|**Тип**<br>Тип данных: Строка|Реализуйте этот параметр, чтобы пользователь может указать тип ресурса, на которой выполняются операции.|
|**URL-адрес**<br>Тип данных: Строка|Реализуйте этот параметр, благодаря которому пользователь может указать унифицированный указатель ресурса (URL).|
|**User**<br>Тип данных: Строка|Реализуйте этот параметр, чтобы пользователь может указать свое имя или имя другого пользователя.|

## <a name="see-also"></a>См. также

[Параметры командлета](./cmdlet-parameters.md)

[Запись командлета Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Пакет SDK для Windows PowerShell](../windows-powershell-reference.md)
