---
ms.date: 06/12/2017
keywords: dsc,powershell,конфигурация,установка
title: Ресурс nxFile в DSC для Linux
ms.openlocfilehash: 80969ba2ea6247fcd616a301d951403a840c851d
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047893"
---
# <a name="dsc-for-linux-nxfile-resource"></a><span data-ttu-id="de8b7-103">Ресурс nxFile в DSC для Linux</span><span class="sxs-lookup"><span data-stu-id="de8b7-103">DSC for Linux nxFile Resource</span></span>

<span data-ttu-id="de8b7-104">Ресурс **nxFile** в настройке требуемого состояния PowerShell предоставляет механизм управления файлами и каталогами на узле Linux.</span><span class="sxs-lookup"><span data-stu-id="de8b7-104">The **nxFile** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage files and directories on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="de8b7-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="de8b7-105">Syntax</span></span>

```
nxFile <string> #ResourceName
{
    DestinationPath = <string>
    [ SourcePath = <string> ]
    [ Ensure = <string> { Absent | Present }  ]
    [ Type = <string> { directory | file | link } ]
    [ Contents = <string> ]
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Recurse = <bool> ]
    [ Force = <bool> ]
    [ Links = <string> { follow | manage } ]
    [ Group = <string> ]
    [ Mode = <string> ]
    [ Owner = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="de8b7-106">Свойства</span><span class="sxs-lookup"><span data-stu-id="de8b7-106">Properties</span></span>

|  <span data-ttu-id="de8b7-107">Свойство</span><span class="sxs-lookup"><span data-stu-id="de8b7-107">Property</span></span> |  <span data-ttu-id="de8b7-108">Описание</span><span class="sxs-lookup"><span data-stu-id="de8b7-108">Description</span></span> |
|---|---|
| <span data-ttu-id="de8b7-109">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="de8b7-109">DestinationPath</span></span>| <span data-ttu-id="de8b7-110">Указывает, в каком расположении нужно проверить состояние файла или каталога.</span><span class="sxs-lookup"><span data-stu-id="de8b7-110">Specifies the location where you want to ensure the state for a file or directory.</span></span>|
| <span data-ttu-id="de8b7-111">SourcePath</span><span class="sxs-lookup"><span data-stu-id="de8b7-111">SourcePath</span></span>| <span data-ttu-id="de8b7-112">Указывает, откуда нужно скопировать файл или папку.</span><span class="sxs-lookup"><span data-stu-id="de8b7-112">Specifies the path from which to copy the file or folder resource.</span></span> <span data-ttu-id="de8b7-113">Этот может быть локальный путь или URL-адрес `http/https/ftp`.</span><span class="sxs-lookup"><span data-stu-id="de8b7-113">This path may be a local path, or an `http/https/ftp` URL.</span></span> <span data-ttu-id="de8b7-114">Удаленные URL-адреса `http/https/ftp` поддерживаются, только если для свойства **Type** выбрано значение file.</span><span class="sxs-lookup"><span data-stu-id="de8b7-114">Remote `http/https/ftp` URLs are only supported when the value of the **Type** property is file.</span></span>|
| <span data-ttu-id="de8b7-115">Ensure</span><span class="sxs-lookup"><span data-stu-id="de8b7-115">Ensure</span></span>| <span data-ttu-id="de8b7-116">Определяет, нужно ли проверять существование файла.</span><span class="sxs-lookup"><span data-stu-id="de8b7-116">Determines whether to check if the file exists.</span></span> <span data-ttu-id="de8b7-117">Чтобы убедиться, что файл существует, укажите для этого свойства значение Present.</span><span class="sxs-lookup"><span data-stu-id="de8b7-117">Set this property to "Present" to ensure the file exists.</span></span> <span data-ttu-id="de8b7-118">Чтобы убедиться, что файл не существует, укажите для этого свойства значение Absent.</span><span class="sxs-lookup"><span data-stu-id="de8b7-118">Set it to "Absent" to ensure the file does not exist.</span></span> <span data-ttu-id="de8b7-119">Значение по умолчанию — Present.</span><span class="sxs-lookup"><span data-stu-id="de8b7-119">The default value is "Present".</span></span>|
| <span data-ttu-id="de8b7-120">Type</span><span class="sxs-lookup"><span data-stu-id="de8b7-120">Type</span></span>| <span data-ttu-id="de8b7-121">Указывает, является ли настраиваемый ресурс каталогом или файлом.</span><span class="sxs-lookup"><span data-stu-id="de8b7-121">Specifies whether the resource being configured is a directory or a file.</span></span> <span data-ttu-id="de8b7-122">Если выбрано значение directory, то ресурс является каталогом,</span><span class="sxs-lookup"><span data-stu-id="de8b7-122">Set this property to "directory" to indicate that the resource is a directory.</span></span> <span data-ttu-id="de8b7-123">а если значение file, то файлом.</span><span class="sxs-lookup"><span data-stu-id="de8b7-123">Set it to "file" to indicate that the resource is a file.</span></span> <span data-ttu-id="de8b7-124">Значение по умолчанию — file.</span><span class="sxs-lookup"><span data-stu-id="de8b7-124">The default value is "file"</span></span>|
| <span data-ttu-id="de8b7-125">Содержимое</span><span class="sxs-lookup"><span data-stu-id="de8b7-125">Contents</span></span>| <span data-ttu-id="de8b7-126">Указывает содержимое файла, например определенную строку.</span><span class="sxs-lookup"><span data-stu-id="de8b7-126">Specifies the contents of a file, such as a particular string.</span></span>|
| <span data-ttu-id="de8b7-127">Контрольная сумма</span><span class="sxs-lookup"><span data-stu-id="de8b7-127">Checksum</span></span>| <span data-ttu-id="de8b7-128">Определяет тип проверки пары файлов на идентичность.</span><span class="sxs-lookup"><span data-stu-id="de8b7-128">Defines the type to use when determining whether two files are the same.</span></span> <span data-ttu-id="de8b7-129">Если свойство **Checksum** не задано, для сравнения используется только имя файла или каталога.</span><span class="sxs-lookup"><span data-stu-id="de8b7-129">If **Checksum** is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="de8b7-130">Значения: ctime, mtime или md5.</span><span class="sxs-lookup"><span data-stu-id="de8b7-130">Values are: "ctime", "mtime", or "md5".</span></span>|
| <span data-ttu-id="de8b7-131">Recurse</span><span class="sxs-lookup"><span data-stu-id="de8b7-131">Recurse</span></span>| <span data-ttu-id="de8b7-132">Указывает, используются ли вложенные папки.</span><span class="sxs-lookup"><span data-stu-id="de8b7-132">Indicates if subdirectories are included.</span></span> <span data-ttu-id="de8b7-133">Если свойство имеет значение **$true**, вложенные папки включаются.</span><span class="sxs-lookup"><span data-stu-id="de8b7-133">Set this property to **$true** to indicate that you want subdirectories to be included.</span></span> <span data-ttu-id="de8b7-134">Значение по умолчанию — **$false**.</span><span class="sxs-lookup"><span data-stu-id="de8b7-134">The default is **$false**.</span></span> <span data-ttu-id="de8b7-135">**Примечание**. Это свойство допустимо только тогда, когда **тип** свойство имеет значение directory.</span><span class="sxs-lookup"><span data-stu-id="de8b7-135">**Note:** This property is only valid when the **Type** property is set to directory.</span></span>|
| <span data-ttu-id="de8b7-136">Force</span><span class="sxs-lookup"><span data-stu-id="de8b7-136">Force</span></span>| <span data-ttu-id="de8b7-137">Определенные операции с файлами (например, перезапись файла или удаление непустого каталога) вызывают ошибку.</span><span class="sxs-lookup"><span data-stu-id="de8b7-137">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="de8b7-138">Свойство **Force** позволяет переопределять такие ошибки.</span><span class="sxs-lookup"><span data-stu-id="de8b7-138">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="de8b7-139">Значение по умолчанию — **$false**.</span><span class="sxs-lookup"><span data-stu-id="de8b7-139">The default value is **$false**.</span></span>|
| <span data-ttu-id="de8b7-140">Ссылки</span><span class="sxs-lookup"><span data-stu-id="de8b7-140">Links</span></span>| <span data-ttu-id="de8b7-141">Определяет желаемое поведение символических ссылок.</span><span class="sxs-lookup"><span data-stu-id="de8b7-141">Specifies the desired behavior for symbolic links.</span></span> <span data-ttu-id="de8b7-142">Если для свойства установлено значение follow, символические ссылки отслеживаются, а к целевым объектам применяются действия (например,</span><span class="sxs-lookup"><span data-stu-id="de8b7-142">Set this property to "follow" to follow symbolic links and act on the links target (for example.</span></span> <span data-ttu-id="de8b7-143">копирование файла вместо ссылки).</span><span class="sxs-lookup"><span data-stu-id="de8b7-143">copy the file instead of the link).</span></span> <span data-ttu-id="de8b7-144">Если установлено значение manage, действие применяется к ссылке (например,</span><span class="sxs-lookup"><span data-stu-id="de8b7-144">Set this property to "manage" to act on the link (for example.</span></span> <span data-ttu-id="de8b7-145">копирование ссылки).</span><span class="sxs-lookup"><span data-stu-id="de8b7-145">copy the link itself).</span></span> <span data-ttu-id="de8b7-146">Если установлено значение ignore, символические ссылки игнорируются.</span><span class="sxs-lookup"><span data-stu-id="de8b7-146">Set this property to "ignore" to ignore symbolic links.</span></span>|
| <span data-ttu-id="de8b7-147">Группа</span><span class="sxs-lookup"><span data-stu-id="de8b7-147">Group</span></span>| <span data-ttu-id="de8b7-148">Имя ресурса **Group** — владельца файла или каталога.</span><span class="sxs-lookup"><span data-stu-id="de8b7-148">The name of the **Group** to own the file or directory.</span></span>|
| <span data-ttu-id="de8b7-149">Режим</span><span class="sxs-lookup"><span data-stu-id="de8b7-149">Mode</span></span>| <span data-ttu-id="de8b7-150">Указывает нужные разрешения для ресурса в восьмеричной или символьной нотации</span><span class="sxs-lookup"><span data-stu-id="de8b7-150">Specifies the desired permissions for the resource, in octal or symbolic notation.</span></span> <span data-ttu-id="de8b7-151">(например, 777 или rwxrwxrwx).</span><span class="sxs-lookup"><span data-stu-id="de8b7-151">(for example, 777 or rwxrwxrwx).</span></span> <span data-ttu-id="de8b7-152">Если используется символьная нотация, не указывайте первый символ, обозначающий каталог или файл.</span><span class="sxs-lookup"><span data-stu-id="de8b7-152">If using symbolic notation, do not provide the first character which indicates directory or file.</span></span>|
| <span data-ttu-id="de8b7-153">DependsOn</span><span class="sxs-lookup"><span data-stu-id="de8b7-153">DependsOn</span></span> | <span data-ttu-id="de8b7-154">Указывает, что перед настройкой этого ресурса необходимо запустить настройку другого ресурса.</span><span class="sxs-lookup"><span data-stu-id="de8b7-154">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="de8b7-155">Например, если **идентификатор** первого запускаемого блока сценария для конфигурации ресурса — **ResourceName**, а его тип — **ResourceType**, то синтаксис использования этого свойства таков: `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="de8b7-155">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="additional-information"></a><span data-ttu-id="de8b7-156">Дополнительные сведения</span><span class="sxs-lookup"><span data-stu-id="de8b7-156">Additional Information</span></span>


<span data-ttu-id="de8b7-157">Linux и Windows используют разные символы разрыва строки в текстовых файлах по умолчанию, что может привести к непредвиденным результатам при настройке некоторых файлов на компьютере Linux с помощью __nxFile__.</span><span class="sxs-lookup"><span data-stu-id="de8b7-157">Linux and Windows use different line break characters in text files by default, and this can cause unexpected results when configuring some files on a Linux computer with __nxFile__.</span></span> <span data-ttu-id="de8b7-158">Избежать проблем из-за непредвиденных символов разрыва строки при работе с содержанием файла Linux можно разными способами:</span><span class="sxs-lookup"><span data-stu-id="de8b7-158">There are multiple ways to manage the content of a Linux file while avoiding issues caused by unexpected line break characters:</span></span>

<span data-ttu-id="de8b7-159">Шаг 1. Скопируйте файл из удаленного источника (HTTP, HTTPS или FTP): создайте файл с нужным содержанием на компьютере Linux и поместите его на веб- или FTP-сервер, доступный для настраиваемого узла.</span><span class="sxs-lookup"><span data-stu-id="de8b7-159">Step 1: Copy the file from a remote source (http, https, or ftp): create a file on Linux with the desired contents, and stage it on a web or ftp server accessible the node(s) you will configure.</span></span> <span data-ttu-id="de8b7-160">Определите свойство __SourcePath__ в ресурсе __nxFile__, указав URL-адрес файла на веб- или FTP-сервере.</span><span class="sxs-lookup"><span data-stu-id="de8b7-160">Define the __SourcePath__ property in the __nxFile__ resource with the web or ftp URL to the file.</span></span>

```
Import-DSCResource -Module nx
Node $Node
{
nxFile resolvConf
{
    SourcePath = "http://10.185.85.11/conf/resolv.conf"
    DestinationPath = "/etc/resolv.conf"
    Mode = "644"
    Type = "file"

}

}
```


<span data-ttu-id="de8b7-161">Шаг 2. Прочтите содержимое файла в сценарии PowerShell с помощью командлета [Get-Content](https://technet.microsoft.com/library/hh849787.aspx), настроив символ переноса строки Linux с помощью свойства __$OFS__.</span><span class="sxs-lookup"><span data-stu-id="de8b7-161">Step 2: Read the file contents in the PowerShell script with [Get-Content](https://technet.microsoft.com/library/hh849787.aspx) after setting the __$OFS__ property to use the Linux line-break character.</span></span>


```
Import-DSCResource -Module nx
Node $Node
{
$OFS = "`n"
$Contents = Get-Content C:\temp\resolv.conf

nxFile resolvConf
{
    DestinationPath = "/etc/resolv.conf"
    Mode = "644"
    Type = "file"
    Contents = "$Contents"
}

}
```


<span data-ttu-id="de8b7-162">Шаг 3. Используйте функцию PowerShell, чтобы заменить Windows, разрывы строк с помощью символов разрыва строки Linux.</span><span class="sxs-lookup"><span data-stu-id="de8b7-162">Step 3: Use a PowerShell function to replace Windows line breaks with Linux line-break characters.</span></span>

```
Function LinuxString($inputStr){
    $outputStr = $inputStr.Replace("`r`n","`n")
    $ouputStr += "`n"
    Return $outputStr
}

Import-DSCResource -Module nx
Node $Node
{

$Contents = @'
search contoso.com
domain contoso.com
nameserver 10.185.85.11
'@

$Contents = LinuxString $Contents

nxFile resolvConf
{
    DestinationPath = "/etc/resolv.conf"
    Mode = "644"
    Type = "file"
    Contents = $Contents

}
}
```

## <a name="example"></a><span data-ttu-id="de8b7-163">Пример</span><span class="sxs-lookup"><span data-stu-id="de8b7-163">Example</span></span>

<span data-ttu-id="de8b7-164">В следующем примере проверяется существование каталога `/opt/mydir` и файла с указанным содержимым в этом каталоге.</span><span class="sxs-lookup"><span data-stu-id="de8b7-164">The following example ensures that the directory `/opt/mydir` exists, and that a file with specified contents exists this directory.</span></span>

```
Import-DSCResource -Module nx

Node $node {
nxFile DirectoryExample
{
   Ensure = "Present"
   DestinationPath = "/opt/mydir"
   Type = "Directory"
}

nxFile FileExample
{
    Ensure = "Present"
    Destinationpath = "/opt/mydir/myfile"
    Contents=@"
#!/bin/bash`necho "hello world"`n
"@
    Mode = “755”
    DependsOn = "[nxFile]DirectoryExample"
}
}
```