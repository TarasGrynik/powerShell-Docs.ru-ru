---
title: Основные понятия Windows PowerShell командлет | Документация Майкрософт
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b3ef3f4-c626-4679-884f-406a37412b3e
caps.latest.revision: 16
ms.openlocfilehash: 2f84c57da7429462c69b2a020d9f8ac04f8d0f35
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855790"
---
# <a name="windows-powershell-cmdlet-concepts"></a>Основные понятия, связанные с командлетами Windows PowerShell

В этом разделе описывается, как работают командлеты.

## <a name="in-this-section"></a>Содержание

Этот раздел содержит следующие темы.

[Рекомендации по разработке командлет](./cmdlet-development-guidelines.md) этот раздел содержит рекомендации по разработке, которые могут использоваться для создания правильного командлетов.

[Объявление класса командлет](./cmdlet-class-declaration.md) в этом разделе описывается объявление класса командлета.

[Утвержденные глаголы для Windows PowerShell команд](./approved-verbs-for-windows-powershell-commands.md) в этом разделе перечислены стандартные командлет команд, которые можно использовать при объявлении класса cmdlet.

[Методы ввода обработки командлета](./cmdlet-input-processing-methods.md) в этом разделе описываются методы, позволяющие командлету, чтобы выполнять операции предварительной обработки, операции обработки ввода и публиковать операции обработки.

[Параметры командлета](./cmdlet-parameters.md) в этом разделе описываются различные типы параметров, которые можно добавить в командлетах.

[Атрибуты командлета](./cmdlet-attributes.md) в этом разделе описываются атрибуты, которые используются для объявления классов .NET Framework как командлеты, для объявления поля, что параметры командлета и объявить правила проверки входных данных для параметров.

[Псевдонимы командлетов](./cmdlet-aliases.md) в этом разделе описываются псевдонимы командлетов.

[Выходные данные командлета](./cmdlet-output.md) в этом разделе описывается тип выходных данных, который может возвращать командлеты и способы определения и отображения объектов, возвращаемых командлетами.

[Регистрация командлетов](./modules-and-snap-ins.md) в этом разделе описывается регистрация командлетов с помощью модулей и оснасток.

[Запрос на подтверждение](./requesting-confirmation-from-cmdlets.md) в этом разделе описывается, как командлеты запросит подтверждение от пользователя, перед внесением изменений в систему.

[Отчеты об ошибках Windows PowerShell](./error-reporting-concepts.md) в этом разделе описывается, как командлеты сообщают прерывающие ошибки и устранимые ошибки, и он описывает способ интерпретации записи об ошибках.

[Фоновые задания](./background-jobs.md) в этом разделе описывается, как командлеты можно выполнять свою работу в рамках фоновых заданий, которые не конфликтуют с помощью команд, которые выполняются в текущем сеансе.

[Вызов командлетов и скриптов в командлет](./invoking-cmdlets-and-scripts-within-a-cmdlet.md) в этом разделе описывается, каким образом командлеты можно вызывать другие командлеты и сценарии изнутри свои методы обработки ввода.

[Командлет задает](./cmdlet-sets.md) в этом разделе описывается использование базовых классов для создания наборов командлетов.

[Состояние сеанса Windows PowerShell](./windows-powershell-session-state.md) в этом разделе описаны состояния сеанса Windows PowerShell.