---
title: Создание удаленного пространства выполнения | Документация Майкрософт
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 057a666f-731b-423d-9d80-7be6b1836244
caps.latest.revision: 5
ms.openlocfilehash: f6cc69df8afe64cea867f5d7f9a7d45753a54d6f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082980"
---
# <a name="creating-remote-runspaces"></a>Создание удаленных пространств выполнения

Команды Windows PowerShell, которые принимают `ComputerName` параметра может выполняться на любом компьютере под управлением Windows PowerShell. Для выполнения команд, которые не принимают `ComputerName` параметр, можно использовать WS-Management для настройки пространства выполнения, который подключается на указанном компьютере и выполните команды на этом компьютере.

## <a name="using-a-wsmanconnection-to-create-a-remote-runspace"></a>Использование WSManConnection для создания в удаленном пространстве выполнения

 Чтобы создать пространство выполнения, который подключается к удаленному компьютеру, необходимо создать [System.Management.Automation.Runspaces.Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) объекта. Целевая конечная точка для подключения указывается установкой [System.Management.Automation.Runspaces.Wsmanconnectioninfo.Connectionuri*](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo.ConnectionUri) свойство объекта. Затем создать пространство выполнения, вызвав [System.Management.Automation.Runspaces.Runspacefactory.Createrunspace*](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory.CreateRunspace) метод, указав [System.Management.Automation.Runspaces.Wsmanconnectioninfo ](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) объекта в виде `connectionInfo` параметра.

 В следующем примере показано, как создать пространство выполнения, который подключается к удаленному компьютеру. В примере `RemoteComputerUri` используется как заполнитель для фактического URI удаленного компьютера.

```csharp
namespace Samples
{
  using System;
  using System.Collections.ObjectModel;
  using System.Management.Automation;            // Windows PowerShell namespace.
  using System.Management.Automation.Runspaces;  // Windows PowerShell namespace.

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class RemoteRunspace02
  {
    /// <summary>
    /// This sample shows how to create a remote runspace that
    /// runs commands on the local computer.
    /// </summary>
    /// <param name="args">Parameter not used.</param>
    private static void Main(string[] args)
    {
      // Create a WSManConnectionInfo object using the default constructor
      // to connect to the "localHost". The WSManConnectionInfo object can
      // also be used to specify connections to remote computers.
      WSManConnectionInfo connectionInfo = new WSManConnectionInfo();

      // Set the OperationTimeout property and OpenTimeout properties.
      // The OperationTimeout property is used to tell Windows PowerShell
      // how long to wait (in milliseconds) before timing out for an
      // operation. The OpenTimeout property is used to tell Windows
      // PowerShell how long to wait (in milliseconds) before timing out
      // while establishing a remote connection.
      connectionInfo.OperationTimeout = 4 * 60 * 1000; // 4 minutes.
      connectionInfo.OpenTimeout = 1 * 60 * 1000; // 1 minute.

      // Create a remote runspace using the connection information.
      //using (Runspace remoteRunspace = RunspaceFactory.CreateRunspace())
      using (Runspace remoteRunspace = RunspaceFactory.CreateRunspace(connectionInfo))
      {
        // Establish the connection by calling the Open() method to open the runspace.
        // The OpenTimeout value set previously will be applied while establishing
        // the connection. Establishing a remote connection involves sending and
        // receiving some data, so the OperationTimeout will also play a role in this process.
          remoteRunspace.Open();

        // Create a PowerShell object to run commands in the remote runspace.
        using (PowerShell powershell = PowerShell.Create())
        {
          powershell.Runspace = remoteRunspace;
          powershell.AddCommand("get-process");
          powershell.Invoke();

          Collection<PSObject> results = powershell.Invoke();

          Console.WriteLine("Process              HandleCount");
          Console.WriteLine("--------------------------------");

          // Display the results.
          foreach (PSObject result in results)
          {
            Console.WriteLine(
                              "{0,-20} {1}",
                              result.Members["ProcessName"].Value,
                              result.Members["HandleCount"].Value);
          }
        }

        // Close the connection. Call the Close() method to close the remote
        // runspace. The Dispose() method (called by using primitive) will call
        // the Close() method if it is not already called.
        remoteRunspace.Close();
      }
    }
  }
}
```
