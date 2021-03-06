---
title: Как добавить имя командлета и краткий обзор раздела справки командлета | Документация Майкрософт
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d0e1eb1-a962-4406-9625-175cfa3364ad
caps.latest.revision: 10
ms.openlocfilehash: f142548be473da15e702f4fa01835609d75b9d51
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083343"
---
# <a name="how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic"></a>Как добавить имя командлета и краткий обзор командлета в раздел справки для командлета

В этом разделе описывается добавление содержимого, которое отображается в разделах справки по командлетам имя и краткие сведения. В файле справки это содержимое добавляется к узлу команду для каждого командлета.

> [!NOTE]
> Для просмотра полного файла справки, откройте один из файлов dll Help.xml расположен в каталоге установки Windows PowerShell. Например файл Microsoft.PowerShell.Commands.Management.dll Help.xml содержимым для нескольких командлетов Windows PowerShell.

### <a name="to-add-the-cmdlet-name-and-a-synopsis"></a>Чтобы добавить имя командлета и краткие сведения

- Справка по командлетам можно отобразить два описания для командлета. Первый приводится краткое описание, которое называется краткий обзор. Второе описание является более подробное описание, которое рассматривается в [Добавление подробное описание для раздела справки командлета](./how-to-add-a-cmdlet-description.md). Оба эти описания должно быть написано как один абзац.

- Не повторять имя командлета в краткий обзор. Где пользователю сообщается о том, что командлет Get-Server возвращает сервер краткий, но не информативные. Вместо этого использовать синонимы и добавления сведений в описание.

  Пример: «Получает объект, представляющий локальный или удаленный компьютер».

- Используйте простой команды, например «get», «создать» и «изменить» в краткий обзор. Старайтесь не использовать «set», поскольку он является неопределенным, и она же такие как «изменение.»

  Пример: «Получает сведения о подписи Authenticode в файле».

- Запись в действительном залоге. Например «использовать объект TimeSpan...» намного более понятны, чем «определяется объектом TimeSpan может использоваться для...»

- При описании командлетов, которые получают объекты, избегайте глагол «display». Несмотря на то, что Windows PowerShell отображает данные командлета, очень важно для пользователей к понятию, командлет возвращает объекты .NET Framework, данные которых может не отображаться. Если вы акцентировать внимание на отображение, пользователь можете не знать, что командлет может вернуть множество других полезных свойств и методов, которые не отображаются.

## <a name="see-also"></a>См. также

 [Пакет SDK для Windows PowerShell](../windows-powershell-reference.md)