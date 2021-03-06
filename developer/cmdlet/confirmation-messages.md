---
title: Подтверждение | Документация Майкрософт
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a886a26d-7730-4586-aeac-fd3f0bc60b88
caps.latest.revision: 8
ms.openlocfilehash: 229725b5b9f1f0082592dcebe11564fd2f630ce1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068374"
---
# <a name="confirmation-messages"></a>Сообщения подтверждения

Ниже приведены различные подтверждающих сообщений, которые могут отображаться в зависимости от того, варианты [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) и [System.Management.Automation.Cmdlet.ShouldContinue ](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) методы, вызываемые.

> [!IMPORTANT]
> Пример кода, показывающий, как для запроса подтверждения, см. в разделе [как подтверждения](./how-to-request-confirmations.md).

## <a name="specifying-the-resource"></a>Указание ресурса

Можно указать ресурс, который собираетесь изменить, вызвав [System.Management.Automation.Cmdlet.Shouldprocess%2A? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) метод. В этом случае указать ресурс с помощью `target` добавлен параметр метода, и операции с Windows PowerShell. В следующее сообщение: текст «MyResource» — это ресурс, обрабатываемого и операции является имя команды, которая выполняет вызов.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

Если пользователь выбирает **Да** или **Да для всех** для подтверждения запроса (как показано в следующем примере), вызов [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)метод будет установлено, что вызывает второе сообщение с подтверждением для отображения.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="specifying-the-operation-and-resource"></a>Задание операции и ресурсов

Можно указать ресурс должен быть изменен и операцию, команда должна выполнить путем вызова [System.Management.Automation.Cmdlet.Shouldprocess%2A? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) метод. В этом случае указать ресурс с помощью `target` параметр и операцию, используя `target` параметра. В следующее сообщение: текст «MyResource» — это ресурс, обрабатываемого, а «MyAction» — операцию для выполнения.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

Если пользователь выбирает **Да** или **Да для всех** к предыдущему сообщению, вызов [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) метод будет установлено, что приводит второе сообщение с подтверждением для отображения.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="see-also"></a>См. также

[Запись командлета Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
