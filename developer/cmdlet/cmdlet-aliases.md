---
title: Псевдонимы командлетов | Документация Майкрософт
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0d70864-33fb-49ce-8054-c41ba19fd554
caps.latest.revision: 11
ms.openlocfilehash: 32f45702cc0d28e6652ef61ebdbe085291013408
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860510"
---
# <a name="cmdlet-aliases"></a>Псевдонимы командлета

Чтобы улучшить взаимодействие с пользователем командлет можно использовать псевдонимы командлетов. Можно добавить псевдонимы для часто используемых командлетов для уменьшения объема ввода и позвольте проще выполнять задачи быстрее. Вы можете включить встроенные псевдонимы в командлеты, или пользователи могут определять свои собственные пользовательских псевдонимов.

Например [Get-Command](/powershell/module/microsoft.powershell.core/get-command) командлет имеет встроенный `gcm` псевдоним. Псевдонимы также можно добавлять имена команд из других языков, чтобы пользователи не имеют дополнительные новые команды.

## <a name="alias-guidelines"></a>Рекомендации по псевдоним

При создании встроенных псевдонимов для командлетов, придерживайтесь следующих рекомендаций.

- Прежде чем назначить псевдонимы, запустите Windows PowerShell, а затем запустите [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) командлет, чтобы просмотреть псевдонимы, которые уже используются.

- Включать префикс псевдоним, который ссылается на команды имя командлета и суффикс псевдоним, ссылающийся на существительное имени командлета. Например, псевдоним `Import-Module` командлет является «ipmo». Список всех команд и их псевдонимы, см. в разделе [глаголов командлетов](./approved-verbs-for-windows-powershell-commands.md).

- Для командлетов, которые имеют ту же команду включать один и тот же префикс псевдонима. Например псевдонимы для всех командлетов Windows PowerShell с глаголом «Get» в имени используйте префикс «g».

- Для командлетов, которые содержат же существительное Включите один и тот же суффикс псевдоним. Например псевдонимы для всех командлетов Windows PowerShell, которые содержат существительное «Сеанс» в имени используйте суффикс «sn».

- Для командлетов, которые эквивалентны команды на других языках используйте имя команды.

- Как правило сделать псевдонимов, как можно более короткими. Убедитесь, что псевдоним имеет хотя бы один символ, уникальных для команды и один символ, уникальных для существительное. Добавьте дополнительные символы, при необходимости, чтобы сделать псевдоним уникальным.

## <a name="see-also"></a>См. также

[Запись командлета Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)