---
ms.date: 06/12/2017
keywords: dsc,powershell,конфигурация,установка
title: Ресурс nxPackage в DSC для Linux
ms.openlocfilehash: 64bb89a95bd6cbaea4e74b8a9979de52428fef3f
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047603"
---
# <a name="dsc-for-linux-nxpackage-resource"></a><span data-ttu-id="d9427-103">Ресурс nxPackage в DSC для Linux</span><span class="sxs-lookup"><span data-stu-id="d9427-103">DSC for Linux nxPackage Resource</span></span>

<span data-ttu-id="d9427-104">Ресурс **nxPackage** в настройке требуемого состояния PowerShell предоставляет механизм управления пакетами на узле Linux.</span><span class="sxs-lookup"><span data-stu-id="d9427-104">The **nxPackage** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage packages on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="d9427-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d9427-105">Syntax</span></span>

```
nxPackage <string> #ResourceName
{
    Name = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ PackageManager = <string> { Yum | Apt | Zypper } ]
    [ PackageGroup = <bool>]
    [ Arguments = <string> ]
    [ ReturnCode = <uint32> ]
    [ LogPath = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="d9427-106">Свойства</span><span class="sxs-lookup"><span data-stu-id="d9427-106">Properties</span></span>

|  <span data-ttu-id="d9427-107">Свойство</span><span class="sxs-lookup"><span data-stu-id="d9427-107">Property</span></span> |  <span data-ttu-id="d9427-108">Описание</span><span class="sxs-lookup"><span data-stu-id="d9427-108">Description</span></span> |
|---|---|
| <span data-ttu-id="d9427-109">Name</span><span class="sxs-lookup"><span data-stu-id="d9427-109">Name</span></span>| <span data-ttu-id="d9427-110">Указывает имя пакета, для которого требуется обеспечить определенное состояние.</span><span class="sxs-lookup"><span data-stu-id="d9427-110">The name of the package for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="d9427-111">Ensure</span><span class="sxs-lookup"><span data-stu-id="d9427-111">Ensure</span></span>| <span data-ttu-id="d9427-112">Определяет, нужно ли проверять существование пакета.</span><span class="sxs-lookup"><span data-stu-id="d9427-112">Determines whether to check if the package exists.</span></span> <span data-ttu-id="d9427-113">Чтобы убедиться, что пакет существует, укажите для этого свойства значение Present.</span><span class="sxs-lookup"><span data-stu-id="d9427-113">Set this property to "Present" to ensure the package exists.</span></span> <span data-ttu-id="d9427-114">Чтобы убедиться, что пакет не существует, укажите для этого свойства значение Absent.</span><span class="sxs-lookup"><span data-stu-id="d9427-114">Set it to "Absent" to ensure the package does not exist.</span></span> <span data-ttu-id="d9427-115">Значение по умолчанию — Present.</span><span class="sxs-lookup"><span data-stu-id="d9427-115">The default value is "Present".</span></span>|
| <span data-ttu-id="d9427-116">PackageManager</span><span class="sxs-lookup"><span data-stu-id="d9427-116">PackageManager</span></span>| <span data-ttu-id="d9427-117">Поддерживаются значения yum, apt и zypper.</span><span class="sxs-lookup"><span data-stu-id="d9427-117">Supported values are "yum", "apt", and "zypper".</span></span> <span data-ttu-id="d9427-118">Указывает, какой диспетчер пакетов нужно использовать при установке пакетов.</span><span class="sxs-lookup"><span data-stu-id="d9427-118">Specifies the package manager to use when installing packages.</span></span> <span data-ttu-id="d9427-119">Если свойство **FilePath** указано, пакет будет установлен по указанному пути.</span><span class="sxs-lookup"><span data-stu-id="d9427-119">If **FilePath** is specified, the provided path will be used to install the package.</span></span> <span data-ttu-id="d9427-120">В противном случае для установки пакета будет использоваться диспетчер пакетов из предварительно настроенного репозитория.</span><span class="sxs-lookup"><span data-stu-id="d9427-120">Otherwise, a Package Manager will be used to install the package from a pre-configured repository.</span></span> <span data-ttu-id="d9427-121">Если ни одно из свойств **PackageManager** и **FilePath** не указано, будет использоваться диспетчер пакетов, предусмотренный для системы по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="d9427-121">If neither **PackageManager** nor **FilePath** are provided, the default package manager for the system will be used.</span></span>|
| <span data-ttu-id="d9427-122">FilePath</span><span class="sxs-lookup"><span data-stu-id="d9427-122">FilePath</span></span>| <span data-ttu-id="d9427-123">Путь к файлу пакета.</span><span class="sxs-lookup"><span data-stu-id="d9427-123">The file path where the package resides</span></span>|
| <span data-ttu-id="d9427-124">PackageGroup</span><span class="sxs-lookup"><span data-stu-id="d9427-124">PackageGroup</span></span>| <span data-ttu-id="d9427-125">Если свойство имеет значение **$true**, в качестве параметра **Name** должно быть задано имя группы пакетов для использования с **PackageManager**.</span><span class="sxs-lookup"><span data-stu-id="d9427-125">If **$true**, the **Name** is expected to be the name of a package group for use with a **PackageManager**.</span></span> <span data-ttu-id="d9427-126">**PackageGroup** не используется, если задано свойство **FilePath**.</span><span class="sxs-lookup"><span data-stu-id="d9427-126">**PacakgeGroup** is not valid when providing a **FilePath**.</span></span>|
| <span data-ttu-id="d9427-127">Аргументы</span><span class="sxs-lookup"><span data-stu-id="d9427-127">Arguments</span></span>| <span data-ttu-id="d9427-128">Строка аргументов, которая будет передана в пакет в указанном виде.</span><span class="sxs-lookup"><span data-stu-id="d9427-128">A string of arguments that will be passed to the package exactly as provided.</span></span>|
| <span data-ttu-id="d9427-129">ReturnCode</span><span class="sxs-lookup"><span data-stu-id="d9427-129">ReturnCode</span></span>| <span data-ttu-id="d9427-130">Ожидаемый код возврата.</span><span class="sxs-lookup"><span data-stu-id="d9427-130">The expected return code.</span></span> <span data-ttu-id="d9427-131">Если фактический код возврата не соответствует указанному здесь значению, настройка вернет ошибку.</span><span class="sxs-lookup"><span data-stu-id="d9427-131">If the actual return code does not match the expected value provided here, the configuration will return an error.</span></span>|
| <span data-ttu-id="d9427-132">DependsOn</span><span class="sxs-lookup"><span data-stu-id="d9427-132">DependsOn</span></span> | <span data-ttu-id="d9427-133">Указывает, что перед настройкой этого ресурса необходимо запустить настройку другого ресурса.</span><span class="sxs-lookup"><span data-stu-id="d9427-133">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="d9427-134">Например, если **идентификатор** первого запускаемого блока сценария для конфигурации ресурса — **ResourceName**, а его тип — **ResourceType**, то синтаксис использования этого свойства таков: `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="d9427-134">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="d9427-135">Пример</span><span class="sxs-lookup"><span data-stu-id="d9427-135">Example</span></span>

<span data-ttu-id="d9427-136">В следующем примере с помощью диспетчера пакетов Yum проверяется, установлен ли пакет с именем httpd на компьютере Linux.</span><span class="sxs-lookup"><span data-stu-id="d9427-136">The following example ensures that the package named "httpd" is installed on a Linux computer, using the “Yum” package manager.</span></span>

```
Import-DSCResource -Module nx

Node $node {
nxPackage httpd
{
    Name = "httpd"
    Ensure = "Present"
    PackageManager = "Yum"
}
}
```