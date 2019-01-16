---
ms.date: 08/14/2018
keywords: powershell,командлет
title: Введение в интегрированную среду сценариев Windows PowerShell
ms.openlocfilehash: 09a28b295855fd2a3c62bba8a681399dae3454f8
ms.sourcegitcommit: 3402a478cf118c11a5642038eb117bc76553e3ab
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2018
ms.locfileid: "53411588"
---
# <a name="the-windows-powershell-ise"></a><span data-ttu-id="aca12-103">Интегрированная среда Сценариев Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="aca12-103">The Windows PowerShell ISE</span></span>

<span data-ttu-id="aca12-104">Интегрированная среда сценариев Windows PowerShell (ISE) является ведущим приложением для Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aca12-104">The Windows PowerShell Integrated Scripting Environment (ISE) is a host application for Windows PowerShell.</span></span> <span data-ttu-id="aca12-105">В интегрированной среде Сценариев можно запускать команды и записывать, тестировать и отлаживать сценарии в одном на базе Windows графическом пользовательском интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="aca12-105">In the ISE, you can run commands and write, test, and debug scripts in a single Windows-based graphic user interface.</span></span> <span data-ttu-id="aca12-106">Интегрированная среда Сценариев предоставляет редактирование нескольких строк, нажатием клавиши TAB, синтаксических конструкций, выборочное выполнение, контекстная справка и поддержка языков справа налево.</span><span class="sxs-lookup"><span data-stu-id="aca12-106">The ISE provides multiline editing, tab completion, syntax coloring, selective execution, context-sensitive help, and support for right-to-left languages.</span></span> <span data-ttu-id="aca12-107">Элементы меню и сочетания клавиш подходят для выполнения большинства тех же задач, которые выполняются в консоли Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aca12-107">Menu items and keyboard shortcuts are mapped to many of the same tasks that you would do in the Windows PowerShell console.</span></span> <span data-ttu-id="aca12-108">Например при отладке скрипта в интегрированной СРЕДЕ вы можете щелкнуть строку кода в области редактирования, чтобы задать точку останова.</span><span class="sxs-lookup"><span data-stu-id="aca12-108">For example, when you debug a script in the ISE, you can right-click on a line of code in the edit pane to set a breakpoint.</span></span>

## <a name="support"></a><span data-ttu-id="aca12-109">Поддержка</span><span class="sxs-lookup"><span data-stu-id="aca12-109">Support</span></span>

<span data-ttu-id="aca12-110">Интегрированная среда Сценариев появилась с помощью Windows PowerShell V2 и снова было разработано с PowerShell версии 3.</span><span class="sxs-lookup"><span data-stu-id="aca12-110">The ISE was first introduced with Windows PowerShell V2 and was re-designed with PowerShell V3.</span></span> <span data-ttu-id="aca12-111">Интегрированная среда Сценариев поддерживается во всех поддерживаемых версиях Windows PowerShell до и включая версии 5.1 для Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aca12-111">The ISE is supported in all supported versions of Windows PowerShell up to and including Windows PowerShell V5.1.</span></span> <span data-ttu-id="aca12-112">Интегрированная среда Сценариев, но находится в режиме maintennce и нет новых функций, скорее всего, для добавления.</span><span class="sxs-lookup"><span data-stu-id="aca12-112">The ISE, however, is in maintennce mode and no new features are likely to be added.</span></span>
<span data-ttu-id="aca12-113">Кроме того не поддерживается для интегрированной среды Сценариев с помощью PowerShell версии 6 и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="aca12-113">Additionally, there is no support for the ISE with PowerShell v6 and beyond.</span></span> <span data-ttu-id="aca12-114">Следует учитывать пользователей, желающих это графическое средство, с которых требуется управление PowerShell scrips и т. д, [Visual Studio Code](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="aca12-114">Users wanting a graphical tool with which to manage PowerShell scrips, etc, should consider [Visual Studio Code](https://code.visualstudio.com/).</span></span>

## <a name="key-features"></a><span data-ttu-id="aca12-115">Ключевые особенности</span><span class="sxs-lookup"><span data-stu-id="aca12-115">Key Features</span></span>

<span data-ttu-id="aca12-116">Ключевые функции в интегрированной среде Сценариев Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="aca12-116">Key features in Windows PowerShell ISE include:</span></span>

- <span data-ttu-id="aca12-117">Редактирование нескольких строк. Чтобы вставить пустую строку под текущей строкой в области команд, нажмите клавиши SHIFT + ВВОД.</span><span class="sxs-lookup"><span data-stu-id="aca12-117">Multiline editing: To insert a blank line under the current line in the Command pane, press SHIFT+ENTER.</span></span>
- <span data-ttu-id="aca12-118">Выборочное выполнение. Чтобы запустить фрагмент сценария, выберите текст, который нужно запустить, и нажмите кнопку **Запустить сценарий**.</span><span class="sxs-lookup"><span data-stu-id="aca12-118">Selective execution: To run part of a script, select the text you want to run, and then click the **Run Script** button.</span></span> <span data-ttu-id="aca12-119">Также можно нажать клавишу F5.</span><span class="sxs-lookup"><span data-stu-id="aca12-119">Or, press F5.</span></span>
- <span data-ttu-id="aca12-120">Контекстная справка. Введите **Invoke-Item** и нажмите клавишу F1.</span><span class="sxs-lookup"><span data-stu-id="aca12-120">Context-sensitive help: Type **Invoke-Item**, and then press F1.</span></span> <span data-ttu-id="aca12-121">Откроется файл справки со ссылкой на статью о командлете **Invoke-Item**.</span><span class="sxs-lookup"><span data-stu-id="aca12-121">The Help file opens to the article for the **Invoke-Item** cmdlet.</span></span>

<span data-ttu-id="aca12-122">Интегрированная среда сценариев Windows PowerShell позволяет настроить некоторые аспекты его представления.</span><span class="sxs-lookup"><span data-stu-id="aca12-122">The Windows PowerShell ISE lets you customize some aspects of its appearance.</span></span> <span data-ttu-id="aca12-123">Она также имеет свой собственный скрипт профиля Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aca12-123">It also has its own Windows PowerShell profile script.</span></span>

## <a name="to-start-the-windows-powershell-ise"></a><span data-ttu-id="aca12-124">Запуск интегрированной среды сценариев Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="aca12-124">To start the Windows PowerShell ISE</span></span>

<span data-ttu-id="aca12-125">Нажмите кнопку **Пуск**, выберите раздел **Windows PowerShell**, а затем щелкните **Интегрированная среда скриптов Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="aca12-125">Click **Start**, select **Windows PowerShell**, and then click **Windows PowerShell ISE**.</span></span>
<span data-ttu-id="aca12-126">Кроме того, можно ввести `powershell_ise.exe` в любой командной оболочке или поле "Выполнить".</span><span class="sxs-lookup"><span data-stu-id="aca12-126">Alternately, you can type `powershell_ise.exe` in any command shell or in the Run box.</span></span>

## <a name="to-get-help-in-the-windows-powershell-ise"></a><span data-ttu-id="aca12-127">Получение справки в интегрированной среде сценариев Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="aca12-127">To get Help in the Windows PowerShell ISE</span></span>

<span data-ttu-id="aca12-128">В меню **Справка** выберите **Справка Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="aca12-128">On the **Help** menu, click **Windows PowerShell Help**.</span></span> <span data-ttu-id="aca12-129">Также можно нажать клавишу F1.</span><span class="sxs-lookup"><span data-stu-id="aca12-129">Or, press F1.</span></span> <span data-ttu-id="aca12-130">В открывшемся файле будет описана интегрированная среда сценариев Windows PowerShell и служба Windows PowerShell, в том числе вся справка, доступная с помощью командлета Get-Help.</span><span class="sxs-lookup"><span data-stu-id="aca12-130">The file that opens describes Windows PowerShell ISE and Windows PowerShell, including all of the help available from the Get-Help cmdlet.</span></span>