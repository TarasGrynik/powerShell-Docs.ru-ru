---
ms.date: 06/05/2017
keywords: powershell,командлет
title: Работа с принтерами
ms.assetid: 4f29ead3-f83b-4706-ac3e-f2154ff38dc5
ms.openlocfilehash: 5638629fdf79371c8eff9ee9194b642034250fff
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403272"
---
# <a name="working-with-printers"></a><span data-ttu-id="155ab-103">Работа с принтерами</span><span class="sxs-lookup"><span data-stu-id="155ab-103">Working with Printers</span></span>

<span data-ttu-id="155ab-104">Windows PowerShell можно использовать для управления принтерами с помощью инструментария WMI и COM-объекта WScript.Network с сервера сценариев Windows.</span><span class="sxs-lookup"><span data-stu-id="155ab-104">You can use Windows PowerShell to manage printers by using WMI and the WScript.Network COM object from WSH.</span></span> <span data-ttu-id="155ab-105">Мы будем использовать сочетание обоих средств, чтобы продемонстрировать выполнение конкретных задач.</span><span class="sxs-lookup"><span data-stu-id="155ab-105">We will use a mix of both tools to demonstrate specific tasks.</span></span>

### <a name="listing-printer-connections"></a><span data-ttu-id="155ab-106">Вывод подключений принтеров</span><span class="sxs-lookup"><span data-stu-id="155ab-106">Listing Printer Connections</span></span>

<span data-ttu-id="155ab-107">Самый простой способ вывести список принтеров, установленных на компьютере, — использовать класс **Win32_Printer** инструментария WMI.</span><span class="sxs-lookup"><span data-stu-id="155ab-107">The simplest way to list the printers installed on a computer is to use the WMI **Win32_Printer** class:</span></span>

```powershell
Get-WmiObject -Class Win32_Printer -ComputerName
```

<span data-ttu-id="155ab-108">Список принтеров можно также вывести с помощью COM-объекта **WScript.Network**, который обычно используется в сценариях сервера сценариев Windows:</span><span class="sxs-lookup"><span data-stu-id="155ab-108">You can also list the printers by using the **WScript.Network** COM object that is typically used in WSH scripts:</span></span>

```powershell
(New-Object -ComObject WScript.Network).EnumPrinterConnections()
```

<span data-ttu-id="155ab-109">Поскольку эта команда возвращает простую коллекцию строк из имен портов и принтеров без отличительных меток, ее непросто интерпретировать.</span><span class="sxs-lookup"><span data-stu-id="155ab-109">Because this command returns a simple string collection of port names and printer device names without any distinguishing labels, it is not easy to interpret.</span></span>

### <a name="adding-a-network-printer"></a><span data-ttu-id="155ab-110">Добавление сетевого принтера</span><span class="sxs-lookup"><span data-stu-id="155ab-110">Adding a Network Printer</span></span>

<span data-ttu-id="155ab-111">Чтобы добавить сетевой принтер, используйте **WScript.Network**:</span><span class="sxs-lookup"><span data-stu-id="155ab-111">To add a new network printer, use **WScript.Network**:</span></span>

```powershell
(New-Object -ComObject WScript.Network).AddWindowsPrinterConnection("\\Printserver01\Xerox5")
```

### <a name="setting-a-default-printer"></a><span data-ttu-id="155ab-112">Установка принтера по умолчанию</span><span class="sxs-lookup"><span data-stu-id="155ab-112">Setting a Default Printer</span></span>

<span data-ttu-id="155ab-113">Чтобы задать принтер по умолчанию с помощью инструментария WMI, найдите принтер в коллекции **Win32_Printer**, а затем вызовите метод **SetDefaultPrinter**.</span><span class="sxs-lookup"><span data-stu-id="155ab-113">To use WMI to set the default printer, find the printer in the **Win32_Printer** collection and then invoke the **SetDefaultPrinter** method:</span></span>

```powershell
(Get-WmiObject -ComputerName . -Class Win32_Printer -Filter "Name='HP LaserJet 5Si'").SetDefaultPrinter()
```

<span data-ttu-id="155ab-114">**WScript.Network** немного проще в использовании, так как содержит метод **SetDefaultPrinter**, который принимает в качестве аргумента только имя принтера:</span><span class="sxs-lookup"><span data-stu-id="155ab-114">**WScript.Network** is a little simpler to use, because it has a **SetDefaultPrinter** method that takes only the printer name as an argument:</span></span>

```powershell
(New-Object -ComObject WScript.Network).SetDefaultPrinter('HP LaserJet 5Si')
```

### <a name="removing-a-printer-connection"></a><span data-ttu-id="155ab-115">Удаление подключения принтера</span><span class="sxs-lookup"><span data-stu-id="155ab-115">Removing a Printer Connection</span></span>

<span data-ttu-id="155ab-116">Чтобы удалить подключение принтера, используйте метод **WScript.Network RemovePrinterConnection**:</span><span class="sxs-lookup"><span data-stu-id="155ab-116">To remove a printer connection, use the **WScript.Network RemovePrinterConnection** method:</span></span>

```powershell
(New-Object -ComObject WScript.Network).RemovePrinterConnection("\\Printserver01\Xerox5")
```