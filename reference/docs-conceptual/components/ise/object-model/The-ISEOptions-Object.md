---
ms.date: 06/05/2017
keywords: powershell,командлет
title: Объект ISEOptions
ms.assetid: 75e2a76f-f3d1-490b-ad5d-e3829946aabb
ms.openlocfilehash: e756da21aaa5465f7fa6a90563b4180f0c89e87b
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403184"
---
# <a name="the-iseoptions-object"></a><span data-ttu-id="29c79-103">Объект ISEOptions</span><span class="sxs-lookup"><span data-stu-id="29c79-103">The ISEOptions Object</span></span>

<span data-ttu-id="29c79-104">Объект **ISEOptions** представляет различные параметры для интегрированной среды сценариев Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="29c79-104">The **ISEOptions** object represents various settings for Windows PowerShell ISE.</span></span> <span data-ttu-id="29c79-105">Он является экземпляром класса **Microsoft.PowerShell.Host.ISE.ISEOptions**.</span><span class="sxs-lookup"><span data-stu-id="29c79-105">It is an instance of the **Microsoft.PowerShell.Host.ISE.ISEOptions** class.</span></span>

<span data-ttu-id="29c79-106">Объект **ISEOptions** предоставляет следующие методы и свойства.</span><span class="sxs-lookup"><span data-stu-id="29c79-106">The **ISEOptions** object provides the following methods and properties.</span></span>

## <a name="methods"></a><span data-ttu-id="29c79-107">Методы</span><span class="sxs-lookup"><span data-stu-id="29c79-107">Methods</span></span>

### <a name="restoredefaultconsoletokencolors"></a><span data-ttu-id="29c79-108">RestoreDefaultConsoleTokenColors \(\)</span><span class="sxs-lookup"><span data-stu-id="29c79-108">RestoreDefaultConsoleTokenColors\(\)</span></span>

<span data-ttu-id="29c79-109">Поддерживается в интегрированной среде сценариев Windows PowerShell 3.0 и более поздних версия и отсутствует в более ранних версиях.</span><span class="sxs-lookup"><span data-stu-id="29c79-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="29c79-110">Восстанавливает значения по умолчанию для цветов маркеров в области консоли.</span><span class="sxs-lookup"><span data-stu-id="29c79-110">Restores the default values of the token colors in the Console pane.</span></span>

```powershell
# Changes the color of the commands in the Console pane to red and then restores it to its default value.
$psISE.Options.ConsoleTokenColors["Command"] = 'red'
$psISE.Options.RestoreDefaultConsoleTokenColors()
```

### <a name="restoredefaults"></a><span data-ttu-id="29c79-111">RestoreDefaults \(\)</span><span class="sxs-lookup"><span data-stu-id="29c79-111">RestoreDefaults\(\)</span></span>

<span data-ttu-id="29c79-112">Поддерживается в интегрированной среде сценариев Windows PowerShell 2.0 и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="29c79-112">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="29c79-113">Восстанавливает значения по умолчанию для всех параметров в области консоли.</span><span class="sxs-lookup"><span data-stu-id="29c79-113">Restores the default values of all options settings in the Console pane.</span></span> <span data-ttu-id="29c79-114">Кроме того, сбрасывает поведение различных предупреждений, включающих стандартный флажок, который отключает повторный вывод сообщения.</span><span class="sxs-lookup"><span data-stu-id="29c79-114">It also resets the behavior of various warning messages that provide the standard check box to prevent the message from being shown again.</span></span>

```powershell
# Changes the background color in the Console pane and then restores it to its default value.
$psISE.Options.ConsolePaneBackgroundColor = 'orange'
$psISE.Options.RestoreDefaults()
```

### <a name="restoredefaulttokencolors"></a><span data-ttu-id="29c79-115">RestoreDefaultTokenColors \(\)</span><span class="sxs-lookup"><span data-stu-id="29c79-115">RestoreDefaultTokenColors\(\)</span></span>

<span data-ttu-id="29c79-116">Поддерживается в интегрированной среде сценариев Windows PowerShell 2.0 и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="29c79-116">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="29c79-117">Восстанавливает значения по умолчанию для цветов маркеров в области сценариев.</span><span class="sxs-lookup"><span data-stu-id="29c79-117">Restores the default values of the token colors in the Script pane.</span></span>

```powershell
# Changes the color of the comments in the Script pane to red and then restores it to its default value.
$psISE.Options.TokenColors["Comment"] = 'red'
$psISE.Options.RestoreDefaultTokenColors()
```

### <a name="restoredefaultxmltokencolors"></a><span data-ttu-id="29c79-118">RestoreDefaultXmlTokenColors \(\)</span><span class="sxs-lookup"><span data-stu-id="29c79-118">RestoreDefaultXmlTokenColors\(\)</span></span>

<span data-ttu-id="29c79-119">Поддерживается в интегрированной среде сценариев Windows PowerShell 3.0 и более поздних версия и отсутствует в более ранних версиях.</span><span class="sxs-lookup"><span data-stu-id="29c79-119">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="29c79-120">Восстанавливает значения по умолчанию для цветов маркеров XML-элементов, отображаемых в интегрированной среде сценариев Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="29c79-120">Restores the default values of the token colors for XML elements that are displayed in Windows PowerShell ISE.</span></span> <span data-ttu-id="29c79-121">См. также [XmlTokenColors](#xmltokencolors).</span><span class="sxs-lookup"><span data-stu-id="29c79-121">Also see [XmlTokenColors](#xmltokencolors).</span></span>

```powershell
# Changes the color of the comments in XML data to red and then restores it to its default value.
$psISE.Options.XmlTokenColors["Comment"] = 'red'
$psISE.Options.RestoreDefaultXmlTokenColors()
```

## <a name="properties"></a><span data-ttu-id="29c79-122">Свойства</span><span class="sxs-lookup"><span data-stu-id="29c79-122">Properties</span></span>

### <a name="autosaveminuteinterval"></a><span data-ttu-id="29c79-123">AutoSaveMinuteInterval</span><span class="sxs-lookup"><span data-stu-id="29c79-123">AutoSaveMinuteInterval</span></span>

<span data-ttu-id="29c79-124">Поддерживается в интегрированной среде сценариев Windows PowerShell 3.0 и более поздних версия и отсутствует в более ранних версиях.</span><span class="sxs-lookup"><span data-stu-id="29c79-124">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="29c79-125">Задает интервал (в минутах) между операциями автоматического сохранения файлов интегрированной средой сценариев Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="29c79-125">Specifies the number of minutes between automatic save operations of your files by Windows PowerShell ISE.</span></span> <span data-ttu-id="29c79-126">Значение по умолчанию — 2 минуты.</span><span class="sxs-lookup"><span data-stu-id="29c79-126">The default value is 2 minutes.</span></span> <span data-ttu-id="29c79-127">Значение представлено целым числом.</span><span class="sxs-lookup"><span data-stu-id="29c79-127">The value is an integer.</span></span>

```powershell
# Changes the number of minutes between automatic save operations to every 3 minutes.
$psISE.Options.AutoSaveMinuteInterval = 3
```

### <a name="commandpanebackgroundcolor"></a><span data-ttu-id="29c79-128">CommandPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="29c79-128">CommandPaneBackgroundColor</span></span>

<span data-ttu-id="29c79-129">Этот компонент присутствует в интегрированной среде сценариев Windows PowerShell 2.0, но был удален или переименован в более поздних версиях интегрированной среды сценариев.</span><span class="sxs-lookup"><span data-stu-id="29c79-129">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="29c79-130">Сведения для более поздних версий см. в разделе [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span><span class="sxs-lookup"><span data-stu-id="29c79-130">For later versions, see [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span></span>

<span data-ttu-id="29c79-131">Задает цвет фона для области команд.</span><span class="sxs-lookup"><span data-stu-id="29c79-131">Specifies the background color for the Command pane.</span></span> <span data-ttu-id="29c79-132">Это экземпляр класса **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="29c79-132">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color of the Command pane to orange.
$psISE.Options.CommandPaneBackgroundColor = 'orange'
```

### <a name="commandpaneup"></a><span data-ttu-id="29c79-133">CommandPaneUp</span><span class="sxs-lookup"><span data-stu-id="29c79-133">CommandPaneUp</span></span>

<span data-ttu-id="29c79-134">Этот компонент присутствует в интегрированной среде сценариев Windows PowerShell 2.0, но был удален или переименован в более поздних версиях интегрированной среды сценариев.</span><span class="sxs-lookup"><span data-stu-id="29c79-134">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>

<span data-ttu-id="29c79-135">Указывает, находится ли область команд над областью вывода.</span><span class="sxs-lookup"><span data-stu-id="29c79-135">Specifies whether the Command pane is located above the Output pane.</span></span>

```powershell
# Moves the Command pane to the top of the screen.
$psISE.Options.CommandPaneUp  = $true
```

### <a name="consolepanebackgroundcolor"></a><span data-ttu-id="29c79-136">ConsolePaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="29c79-136">ConsolePaneBackgroundColor</span></span>

<span data-ttu-id="29c79-137">Поддерживается в интегрированной среде сценариев Windows PowerShell 3.0 и более поздних версия и отсутствует в более ранних версиях.</span><span class="sxs-lookup"><span data-stu-id="29c79-137">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="29c79-138">Задает цвет фона для области консоли.</span><span class="sxs-lookup"><span data-stu-id="29c79-138">Specifies the background color for the Console pane.</span></span> <span data-ttu-id="29c79-139">Это экземпляр класса **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="29c79-139">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color of the Console pane to red.
$psISE.Options.ConsolePaneBackgroundColor = 'red'
```

### <a name="consolepaneforegroundcolor"></a><span data-ttu-id="29c79-140">ConsolePaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="29c79-140">ConsolePaneForegroundColor</span></span>

<span data-ttu-id="29c79-141">Поддерживается в интегрированной среде сценариев Windows PowerShell 3.0 и более поздних версия и отсутствует в более ранних версиях.</span><span class="sxs-lookup"><span data-stu-id="29c79-141">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="29c79-142">Задает цвет переднего плана для текста в области консоли.</span><span class="sxs-lookup"><span data-stu-id="29c79-142">Specifies the foreground color of the text in the Console pane.</span></span>

```powershell
# Changes the foreground color of the text in the Console pane to yellow.
$psISE.Options.ConsolePaneForegroundColor  = 'yellow'
```

### <a name="consolepanetextbackgroundcolor"></a><span data-ttu-id="29c79-143">ConsolePaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="29c79-143">ConsolePaneTextBackgroundColor</span></span>

<span data-ttu-id="29c79-144">Поддерживается в интегрированной среде сценариев Windows PowerShell 3.0 и более поздних версия и отсутствует в более ранних версиях.</span><span class="sxs-lookup"><span data-stu-id="29c79-144">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="29c79-145">Задает цвет фона для текста в области консоли.</span><span class="sxs-lookup"><span data-stu-id="29c79-145">Specifies the background color of the text in the Console pane.</span></span>

```powershell
# Changes the background color of the Console pane text to pink.
$psISE.Options.ConsolePaneTextBackgroundColor = 'pink'
```

### <a name="consoletokencolors"></a><span data-ttu-id="29c79-146">ConsoleTokenColors</span><span class="sxs-lookup"><span data-stu-id="29c79-146">ConsoleTokenColors</span></span>

<span data-ttu-id="29c79-147">Поддерживается в интегрированной среде сценариев Windows PowerShell 3.0 и более поздних версия и отсутствует в более ранних версиях.</span><span class="sxs-lookup"><span data-stu-id="29c79-147">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="29c79-148">Задает цвета маркеров IntelliSense в области консоли интегрированной среды сценариев Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="29c79-148">Specifies the colors of the IntelliSense tokens in the Windows PowerShell ISE Console pane.</span></span> <span data-ttu-id="29c79-149">Это свойство является объектом словаря, который содержит пары "имя — значение" для типов и цветов маркеров для области консоли.</span><span class="sxs-lookup"><span data-stu-id="29c79-149">This property is a dictionary object that contains name/value pairs of token types and colors for the Console pane.</span></span> <span data-ttu-id="29c79-150">Сведения об изменении цвета маркеров IntelliSense в области сценариев см. в разделе [TokenColors](#tokencolors).</span><span class="sxs-lookup"><span data-stu-id="29c79-150">To change the colors of the IntelliSense tokens in the Script pane, see [TokenColors](#tokencolors).</span></span> <span data-ttu-id="29c79-151">Сведения о восстановлении значений по умолчанию для цветов см. в разделе [RestoreDefaultConsoleTokenColors](#restoredefaultconsoletokencolors).</span><span class="sxs-lookup"><span data-stu-id="29c79-151">To reset the colors to the default values, see [RestoreDefaultConsoleTokenColors](#restoredefaultconsoletokencolors).</span></span> <span data-ttu-id="29c79-152">Можно задать цвета маркера в следующих целях: Атрибут, команды, CommandArgument, CommandParameter, комментарий, GroupEnd, GroupStart, ключевое слово, LineContinuation, LoopLabel, член, символ новой строки, номер, оператор, положение, StatementSeparator, строки, тип, Unknown, переменной.</span><span class="sxs-lookup"><span data-stu-id="29c79-152">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span>

```powershell
# Sets the color of commands to green.
$psISE.Options.ConsoleTokenColors["Command"] = 'green'
# Sets the color of keywords to magenta.
$psISE.Options.ConsoleTokenColors["Keyword"] = 'magenta'
```

### <a name="debugbackgroundcolor"></a><span data-ttu-id="29c79-153">DebugBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="29c79-153">DebugBackgroundColor</span></span>

<span data-ttu-id="29c79-154">Поддерживается в интегрированной среде сценариев Windows PowerShell 2.0 и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="29c79-154">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="29c79-155">Задает цвет фона для сообщений отладки, отображаемых в области консоли.</span><span class="sxs-lookup"><span data-stu-id="29c79-155">Specifies the background color for the debug text that appears in the Console pane.</span></span> <span data-ttu-id="29c79-156">Это экземпляр класса **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="29c79-156">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color for the debug text that appears in the Console pane to blue.
$psISE.Options.DebugBackgroundColor = '#0000FF'
```

### <a name="debugforegroundcolor"></a><span data-ttu-id="29c79-157">DebugForegroundColor</span><span class="sxs-lookup"><span data-stu-id="29c79-157">DebugForegroundColor</span></span>

<span data-ttu-id="29c79-158">Поддерживается в интегрированной среде сценариев Windows PowerShell 2.0 и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="29c79-158">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="29c79-159">Задает цвет переднего плана для сообщений отладки, отображаемых в области консоли.</span><span class="sxs-lookup"><span data-stu-id="29c79-159">Specifies the foreground color for the debug text that appears in the Console pane.</span></span> <span data-ttu-id="29c79-160">Это экземпляр класса **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="29c79-160">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the foreground color for the debug text that appears in the Console pane to yellow.
$psISE.Options.DebugForegroundColor = 'yellow'
```

### <a name="defaultoptions"></a><span data-ttu-id="29c79-161">DefaultOptions</span><span class="sxs-lookup"><span data-stu-id="29c79-161">DefaultOptions</span></span>

<span data-ttu-id="29c79-162">Поддерживается в интегрированной среде сценариев Windows PowerShell 2.0 и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="29c79-162">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="29c79-163">Коллекция свойств, задающих значения по умолчанию, используемые при выполнении методов сброса (Reset).</span><span class="sxs-lookup"><span data-stu-id="29c79-163">A collection of properties that specify the default values to be used when the Reset methods are used.</span></span>

```powershell
# Displays the name of the default options. This example is from ISE 4.0.
$psISE.Options.DefaultOptions

SelectedScriptPaneState                   : Top
ShowDefaultSnippets                       : True
ShowToolBar                               : True
ShowOutlining                             : True
ShowLineNumbers                           : True
TokenColors                               : {[Attribute, #FF00BFFF], [Command, #FF0000FF], [CommandArgument, #FF8A2BE2], [CommandParameter, #FF000080]...}
ConsoleTokenColors                        : {[Attribute, #FFB0C4DE], [Command, #FFE0FFFF], [CommandArgument, #FFEE82EE], [CommandParameter, #FFFFE4B5]...}
XmlTokenColors                            : {[Comment, #FF006400], [CommentDelimiter, #FF008000], [ElementName, #FF8B0000], [MarkupExtension, #FFFF8C00]...}
DefaultOptions                            : Microsoft.PowerShell.Host.ISE.ISEOptions
FontSize                                  : 9
Zoom                                      : 100
FontName                                  : Lucida Console
ErrorForegroundColor                      : #FFFF0000
ErrorBackgroundColor                      : #00FFFFFF
WarningForegroundColor                    : #FFFF8C00
WarningBackgroundColor                    : #00FFFFFF
VerboseForegroundColor                    : #FF00FFFF
VerboseBackgroundColor                    : #00FFFFFF
DebugForegroundColor                      : #FF00FFFF
DebugBackgroundColor                      : #00FFFFFF
ConsolePaneBackgroundColor                : #FF012456
ConsolePaneTextBackgroundColor            : #FF012456
ConsolePaneForegroundColor                : #FFF5F5F5
ScriptPaneBackgroundColor                 : #FFFFFFFF
ScriptPaneForegroundColor                 : #FF000000
ShowWarningForDuplicateFiles              : True
ShowWarningBeforeSavingOnRun              : True
UseLocalHelp                              : True
AutoSaveMinuteInterval                    : 2
MruCount                                  : 10
ShowIntellisenseInConsolePane             : True
ShowIntellisenseInScriptPane              : True
UseEnterToSelectInConsolePaneIntellisense : True
UseEnterToSelectInScriptPaneIntellisense  : True
IntellisenseTimeoutInSeconds              : 3
```

### <a name="errorbackgroundcolor"></a><span data-ttu-id="29c79-164">ErrorBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="29c79-164">ErrorBackgroundColor</span></span>

<span data-ttu-id="29c79-165">Поддерживается в интегрированной среде сценариев Windows PowerShell 2.0 и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="29c79-165">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="29c79-166">Задает цвет фона для сообщений об ошибках, отображаемых в области консоли.</span><span class="sxs-lookup"><span data-stu-id="29c79-166">Specifies the background color for error text that appears in the Console pane.</span></span> <span data-ttu-id="29c79-167">Это экземпляр класса **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="29c79-167">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color for the error text that appears in the Console pane to black.
$psISE.Options.ErrorBackgroundColor = 'black'
```

### <a name="errorforegroundcolor"></a><span data-ttu-id="29c79-168">ErrorForegroundColor</span><span class="sxs-lookup"><span data-stu-id="29c79-168">ErrorForegroundColor</span></span>

<span data-ttu-id="29c79-169">Поддерживается в интегрированной среде сценариев Windows PowerShell 2.0 и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="29c79-169">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="29c79-170">Задает цвет переднего плана для сообщений об ошибках, отображаемых в области консоли.</span><span class="sxs-lookup"><span data-stu-id="29c79-170">Specifies the foreground color for error text that appears in the Console pane.</span></span> <span data-ttu-id="29c79-171">Это экземпляр класса **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="29c79-171">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the foreground color for the error text that appears in the console pane to green.
$psISE.Options.ErrorForegroundColor = 'green'
```

### <a name="fontname"></a><span data-ttu-id="29c79-172">FontName</span><span class="sxs-lookup"><span data-stu-id="29c79-172">FontName</span></span>

<span data-ttu-id="29c79-173">Поддерживается в интегрированной среде сценариев Windows PowerShell 2.0 и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="29c79-173">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="29c79-174">Задает название текущего шрифта в области сценариев и в области консоли.</span><span class="sxs-lookup"><span data-stu-id="29c79-174">Specifies the font name currently in use in both the Script pane and the Console pane.</span></span>

```powershell
# Changes the font used in both panes.
$psISE.Options.FontName = 'Courier New'
```

### <a name="fontsize"></a><span data-ttu-id="29c79-175">FontSize</span><span class="sxs-lookup"><span data-stu-id="29c79-175">FontSize</span></span>

<span data-ttu-id="29c79-176">Поддерживается в интегрированной среде сценариев Windows PowerShell 2.0 и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="29c79-176">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="29c79-177">Указывает размер шрифта в виде целого числа.</span><span class="sxs-lookup"><span data-stu-id="29c79-177">Specifies the font size as an integer.</span></span> <span data-ttu-id="29c79-178">Используется в области сценариев, области команд и области вывода.</span><span class="sxs-lookup"><span data-stu-id="29c79-178">It is used in the Script pane, the Command pane, and the Output pane.</span></span> <span data-ttu-id="29c79-179">Допустимый диапазон значений — от 8 до 32.</span><span class="sxs-lookup"><span data-stu-id="29c79-179">The valid range of values is 8 through 32.</span></span>

```powershell
# Changes the font size in all panes.
$psISE.Options.FontSize = 20
```

### <a name="intellisensetimeoutinseconds"></a><span data-ttu-id="29c79-180">IntellisenseTimeoutInSeconds</span><span class="sxs-lookup"><span data-stu-id="29c79-180">IntellisenseTimeoutInSeconds</span></span>

<span data-ttu-id="29c79-181">Поддерживается в интегрированной среде сценариев Windows PowerShell 3.0 и более поздних версия и отсутствует в более ранних версиях.</span><span class="sxs-lookup"><span data-stu-id="29c79-181">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="29c79-182">Указывает интервал (в секундах), в течение которого IntelliSense пытается разрешить текущий вводимый текст.</span><span class="sxs-lookup"><span data-stu-id="29c79-182">Specifies the number of seconds that IntelliSense uses to try to resolve the currently typed text.</span></span> <span data-ttu-id="29c79-183">По завершении указанного интервала время ожидания IntelliSense истекает, и компонент позволяет продолжить ввод текста.</span><span class="sxs-lookup"><span data-stu-id="29c79-183">After this number of seconds, IntelliSense times out and enables you to continue typing.</span></span> <span data-ttu-id="29c79-184">Значение по умолчанию — 3 секунды.</span><span class="sxs-lookup"><span data-stu-id="29c79-184">The default value is 3 seconds.</span></span> <span data-ttu-id="29c79-185">Значение представлено целым числом.</span><span class="sxs-lookup"><span data-stu-id="29c79-185">The value is an integer.</span></span>

```powershell
# Changes the number of seconds for IntelliSense syntax recognition to 5.
$psISE.Options.IntellisenseTimeoutInSeconds = 5
```

### <a name="mrucount"></a><span data-ttu-id="29c79-186">MruCount</span><span class="sxs-lookup"><span data-stu-id="29c79-186">MruCount</span></span>

<span data-ttu-id="29c79-187">Поддерживается в интегрированной среде сценариев Windows PowerShell 3.0 и более поздних версия и отсутствует в более ранних версиях.</span><span class="sxs-lookup"><span data-stu-id="29c79-187">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="29c79-188">Задает число недавно открывавшихся файлов, которые интегрированная среда сценариев Windows PowerShell отслеживает и отображает в нижней части меню **Открытие файла**.</span><span class="sxs-lookup"><span data-stu-id="29c79-188">Specifies the number of recently opened files that Windows PowerShell ISE tracks and displays at the bottom of the **File Open** menu.</span></span> <span data-ttu-id="29c79-189">Значение по умолчанию — 10.</span><span class="sxs-lookup"><span data-stu-id="29c79-189">The default value is 10.</span></span> <span data-ttu-id="29c79-190">Значение представлено целым числом.</span><span class="sxs-lookup"><span data-stu-id="29c79-190">The value is an integer.</span></span>

```powershell
# Changes the number of recently used files that appear at the bottom of the File Open menu to 5.
$psISE.Options.MruCount = 5
```

### <a name="outputpanebackgroundcolor"></a><span data-ttu-id="29c79-191">OutputPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="29c79-191">OutputPaneBackgroundColor</span></span>

<span data-ttu-id="29c79-192">Этот компонент присутствует в интегрированной среде сценариев Windows PowerShell 2.0, но был удален или переименован в более поздних версиях интегрированной среды сценариев.</span><span class="sxs-lookup"><span data-stu-id="29c79-192">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="29c79-193">Сведения для более поздних версий см. в разделе [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span><span class="sxs-lookup"><span data-stu-id="29c79-193">For later versions, see [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span></span>

<span data-ttu-id="29c79-194">Свойство для чтения и записи, которое получает или задает цвет фона самой области вывода.</span><span class="sxs-lookup"><span data-stu-id="29c79-194">The read/write property that gets or sets the background color for the Output pane itself.</span></span> <span data-ttu-id="29c79-195">Это экземпляр класса **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="29c79-195">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color of the Output pane to gold.
$psISE.Options.OutputPaneForegroundColor = 'gold'
```

### <a name="outputpanetextforegroundcolor"></a><span data-ttu-id="29c79-196">OutputPaneTextForegroundColor</span><span class="sxs-lookup"><span data-stu-id="29c79-196">OutputPaneTextForegroundColor</span></span>

<span data-ttu-id="29c79-197">Этот компонент присутствует в интегрированной среде сценариев Windows PowerShell 2.0, но был удален или переименован в более поздних версиях интегрированной среды сценариев.</span><span class="sxs-lookup"><span data-stu-id="29c79-197">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="29c79-198">Сведения для более поздних версий см. в разделе [ConsolePaneForegroundColor](#consolepaneforegroundcolor).</span><span class="sxs-lookup"><span data-stu-id="29c79-198">For later versions, see [ConsolePaneForegroundColor](#consolepaneforegroundcolor).</span></span>

<span data-ttu-id="29c79-199">Свойство для чтения и записи, которое изменяет цвет переднего плана текста в области вывода в интегрированной среде сценариев Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="29c79-199">The read/write property that changes the foreground color of the text in the Output pane in Windows PowerShell ISE 2.0.</span></span>

```powershell
# Changes the foreground color of the text in the Output Pane to blue.
$psISE.Options.OutputPaneTextForegroundColor  = 'blue'
```

### <a name="outputpanetextbackgroundcolor"></a><span data-ttu-id="29c79-200">OutputPaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="29c79-200">OutputPaneTextBackgroundColor</span></span>

<span data-ttu-id="29c79-201">Этот компонент присутствует в интегрированной среде сценариев Windows PowerShell 2.0, но был удален или переименован в более поздних версиях интегрированной среды сценариев.</span><span class="sxs-lookup"><span data-stu-id="29c79-201">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="29c79-202">Сведения для более поздних версий см. в разделе [ConsolePaneTextBackgroundColor](#consolepanetextbackgroundcolor).</span><span class="sxs-lookup"><span data-stu-id="29c79-202">For later versions, see [ConsolePaneTextBackgroundColor](#consolepanetextbackgroundcolor).</span></span>

<span data-ttu-id="29c79-203">Свойство для чтения и записи, которое изменяет цвет фона текста в области вывода.</span><span class="sxs-lookup"><span data-stu-id="29c79-203">The read/write property that changes the background color of the text in the Output pane.</span></span>

```powershell
# Changes the background color of the Output pane text to pink.
$psISE.Options.OutputPaneTextBackgroundColor = 'pink'
```

### <a name="scriptpanebackgroundcolor"></a><span data-ttu-id="29c79-204">ScriptPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="29c79-204">ScriptPaneBackgroundColor</span></span>

<span data-ttu-id="29c79-205">Поддерживается в интегрированной среде сценариев Windows PowerShell 2.0 и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="29c79-205">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="29c79-206">Свойство для чтения и записи, которое получает или задает цвет фона для файлов.</span><span class="sxs-lookup"><span data-stu-id="29c79-206">The read/write property that gets or sets the background color for files.</span></span> <span data-ttu-id="29c79-207">Это экземпляр класса **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="29c79-207">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Sets the color of the script pane background to yellow.
$psISE.Options.ScriptPaneBackgroundColor = 'yellow'
```

### <a name="scriptpaneforegroundcolor"></a><span data-ttu-id="29c79-208">ScriptPaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="29c79-208">ScriptPaneForegroundColor</span></span>

<span data-ttu-id="29c79-209">Поддерживается в интегрированной среде сценариев Windows PowerShell 2.0 и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="29c79-209">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="29c79-210">Свойство для чтения и записи, которое получает или задает цвет переднего плана для файлов, не являющихся сценариями, в области сценариев.</span><span class="sxs-lookup"><span data-stu-id="29c79-210">The read/write property that gets or sets the foreground color for non-script files in the Script pane.</span></span>
<span data-ttu-id="29c79-211">Чтобы задать цвет переднего плана для файлов сценариев, используйте [TokenColors](#tokencolors).</span><span class="sxs-lookup"><span data-stu-id="29c79-211">To set the foreground color for script files, use the [TokenColors](#tokencolors).</span></span>

```powershell
# Sets the foreground to color of non-script files in the script pane to green.
$psISE.Options.ScriptPaneBackgroundColor = 'green'
```

### <a name="selectedscriptpanestate"></a><span data-ttu-id="29c79-212">SelectedScriptPaneState</span><span class="sxs-lookup"><span data-stu-id="29c79-212">SelectedScriptPaneState</span></span>

<span data-ttu-id="29c79-213">Поддерживается в интегрированной среде сценариев Windows PowerShell 2.0 и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="29c79-213">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="29c79-214">Свойство для чтения и записи, которое получает или задает положение области сценариев на экране.</span><span class="sxs-lookup"><span data-stu-id="29c79-214">The read/write property that gets or sets the position of the Script pane on the display.</span></span> <span data-ttu-id="29c79-215">Строка может иметь значение Maximized, Top или Right.</span><span class="sxs-lookup"><span data-stu-id="29c79-215">The string can be either 'Maximized', 'Top', or 'Right'.</span></span>

```powershell
# Moves the Script Pane to the top.
$psISE.Options.SelectedScriptPaneState = 'Top'
# Moves the Script Pane to the right.
$psISE.Options.SelectedScriptPaneState = 'Right'
# Maximizes the Script Pane
$psISE.Options.SelectedScriptPaneState = 'Maximized'
```

### <a name="showdefaultsnippets"></a><span data-ttu-id="29c79-216">ShowDefaultSnippets</span><span class="sxs-lookup"><span data-stu-id="29c79-216">ShowDefaultSnippets</span></span>

<span data-ttu-id="29c79-217">Поддерживается в интегрированной среде сценариев Windows PowerShell 3.0 и более поздних версия и отсутствует в более ранних версиях.</span><span class="sxs-lookup"><span data-stu-id="29c79-217">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="29c79-218">Указывает, содержит ли список фрагментов **CTRL+J** начальный набор, который включен в Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="29c79-218">Specifies whether the **CTRL+J** list of snippets includes the starter set that is included in Windows PowerShell.</span></span> <span data-ttu-id="29c79-219">Если задано значение **$false**, в списке **CTRL+J** отображаются только определенные пользователем фрагменты.</span><span class="sxs-lookup"><span data-stu-id="29c79-219">When set to **$false**, only user-defined snippets appear in the **CTRL+J** list.</span></span> <span data-ttu-id="29c79-220">По умолчанию используется значение **$true**.</span><span class="sxs-lookup"><span data-stu-id="29c79-220">The default value is **$true**.</span></span>

```powershell
# Hide the default snippets from the CTRL+J list.
$psISE.Options.ShowDefaultSnippets = $false
```

### <a name="showintellisenseinconsolepane"></a><span data-ttu-id="29c79-221">ShowIntellisenseInConsolePane</span><span class="sxs-lookup"><span data-stu-id="29c79-221">ShowIntellisenseInConsolePane</span></span>

<span data-ttu-id="29c79-222">Поддерживается в интегрированной среде сценариев Windows PowerShell 3.0 и более поздних версия и отсутствует в более ранних версиях.</span><span class="sxs-lookup"><span data-stu-id="29c79-222">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="29c79-223">Указывает, предлагает ли IntelliSense синтаксис, параметры и значения в области консоли.</span><span class="sxs-lookup"><span data-stu-id="29c79-223">Specifies whether IntelliSense offers syntax, parameter, and value suggestions in the Console pane.</span></span> <span data-ttu-id="29c79-224">По умолчанию используется значение **$true**.</span><span class="sxs-lookup"><span data-stu-id="29c79-224">The default value is **$true**.</span></span>

```powershell
# Turn off IntelliSense in the console pane.
$psISE.Options.ShowIntellisenseInConsolePane = $false
```

### <a name="showintellisenseinscriptpane"></a><span data-ttu-id="29c79-225">ShowIntellisenseInScriptPane</span><span class="sxs-lookup"><span data-stu-id="29c79-225">ShowIntellisenseInScriptPane</span></span>

<span data-ttu-id="29c79-226">Поддерживается в интегрированной среде сценариев Windows PowerShell 3.0 и более поздних версия и отсутствует в более ранних версиях.</span><span class="sxs-lookup"><span data-stu-id="29c79-226">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="29c79-227">Указывает, предлагает ли IntelliSense синтаксис, параметры и значения в области сценариев.</span><span class="sxs-lookup"><span data-stu-id="29c79-227">Specifies whether IntelliSense offers syntax, parameter, and value suggestions in the Script pane.</span></span> <span data-ttu-id="29c79-228">По умолчанию используется значение **$true**.</span><span class="sxs-lookup"><span data-stu-id="29c79-228">The default value is **$true**.</span></span>

```powershell
# Turn off IntelliSense in the Script pane.
$psISE.Options.ShowIntellisenseInScriptPane = $false
```

### <a name="showlinenumbers"></a><span data-ttu-id="29c79-229">ShowLineNumbers</span><span class="sxs-lookup"><span data-stu-id="29c79-229">ShowLineNumbers</span></span>

<span data-ttu-id="29c79-230">Поддерживается в интегрированной среде сценариев Windows PowerShell 3.0 и более поздних версия и отсутствует в более ранних версиях.</span><span class="sxs-lookup"><span data-stu-id="29c79-230">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="29c79-231">Указывает, отображаются ли в левом поле области сценариев номера строк.</span><span class="sxs-lookup"><span data-stu-id="29c79-231">Specifies whether the Script pane displays line numbers in the left margin.</span></span> <span data-ttu-id="29c79-232">По умолчанию используется значение **$true**.</span><span class="sxs-lookup"><span data-stu-id="29c79-232">The default value is **$true**.</span></span>

```powershell
# Turn off line numbers in the Script pane.
$psISE.Options.ShowLineNumbers = $false
```

### <a name="showoutlining"></a><span data-ttu-id="29c79-233">ShowOutlining</span><span class="sxs-lookup"><span data-stu-id="29c79-233">ShowOutlining</span></span>

<span data-ttu-id="29c79-234">Поддерживается в интегрированной среде сценариев Windows PowerShell 3.0 и более поздних версия и отсутствует в более ранних версиях.</span><span class="sxs-lookup"><span data-stu-id="29c79-234">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="29c79-235">Указывает, отображаются ли в области сценариев расширяемые и свертываемые скобки рядом с фрагментами кода в левом поле.</span><span class="sxs-lookup"><span data-stu-id="29c79-235">Specifies whether the Script pane displays expandable and collapsible brackets next to sections of code in the left margin.</span></span> <span data-ttu-id="29c79-236">Когда они отображаются, можно щелкнуть значок "минус" \(-\) рядом с блоком текста, чтобы свернуть, или значок "плюс" \(+\), чтобы развернуть блок текста.</span><span class="sxs-lookup"><span data-stu-id="29c79-236">When they are displayed, you can click the minus \(-\) icons next to a block of text to collapse it or click the plus \(+\) icon to expand a block of text.</span></span> <span data-ttu-id="29c79-237">По умолчанию используется значение **$true**.</span><span class="sxs-lookup"><span data-stu-id="29c79-237">The default value is **$true**.</span></span>

```powershell
# Turn off outlining in the Script pane.
$psISE.Options.ShowOutlining = $false
```

### <a name="showtoolbar"></a><span data-ttu-id="29c79-238">ShowToolBar</span><span class="sxs-lookup"><span data-stu-id="29c79-238">ShowToolBar</span></span>

<span data-ttu-id="29c79-239">Поддерживается в интегрированной среде сценариев Windows PowerShell 2.0 и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="29c79-239">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="29c79-240">Указывает, отображается ли в верхней части окна интегрированной среды сценариев Windows PowerShell панель инструментов ISE.</span><span class="sxs-lookup"><span data-stu-id="29c79-240">Specifies whether the ISE toolbar appears at the top of the Windows PowerShell ISE window.</span></span> <span data-ttu-id="29c79-241">По умолчанию используется значение **$true**.</span><span class="sxs-lookup"><span data-stu-id="29c79-241">The default value is **$true**.</span></span>

```powershell
# Show the toolbar.
$psISE.Options.ShowToolBar = $true
```

### <a name="showwarningbeforesavingonrun"></a><span data-ttu-id="29c79-242">ShowWarningBeforeSavingOnRun</span><span class="sxs-lookup"><span data-stu-id="29c79-242">ShowWarningBeforeSavingOnRun</span></span>

<span data-ttu-id="29c79-243">Поддерживается в интегрированной среде сценариев Windows PowerShell 2.0 и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="29c79-243">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="29c79-244">Указывает, отображается ли предупреждение, когда сценарий сохраняется автоматически перед запуском.</span><span class="sxs-lookup"><span data-stu-id="29c79-244">Specifies whether a warning message appears when a script is saved automatically before it is run.</span></span> <span data-ttu-id="29c79-245">По умолчанию используется значение **$true**.</span><span class="sxs-lookup"><span data-stu-id="29c79-245">The default value is **$true**.</span></span>

```powershell
# Enable the warning message when an attempt
# is made to run a script without saving it first.
$psISE.Options.ShowWarningBeforeSavingOnRun = $true
```

### <a name="showwarningforduplicatefiles"></a><span data-ttu-id="29c79-246">ShowWarningForDuplicateFiles</span><span class="sxs-lookup"><span data-stu-id="29c79-246">ShowWarningForDuplicateFiles</span></span>

<span data-ttu-id="29c79-247">Поддерживается в интегрированной среде сценариев Windows PowerShell 2.0 и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="29c79-247">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="29c79-248">Указывает, отображается ли предупреждение при открытии одного и того же файла на разных вкладках PowerShell.</span><span class="sxs-lookup"><span data-stu-id="29c79-248">Specifies whether a warning message appears when the same file is opened in different PowerShell tabs.</span></span> <span data-ttu-id="29c79-249">Если значение **$true**, чтобы открыть тот же файл на нескольких вкладках отображается сообщение: «Копию этот файл открыт в другой вкладке Windows PowerShell. Изменения, внесенные в данный файл, отразятся на всех его открытых копиях".</span><span class="sxs-lookup"><span data-stu-id="29c79-249">If set to **$true**, to open the same file in multiple tabs displays this message: "A copy of this file is open in another Windows PowerShell tab. Changes made to this file will affect all open copies."</span></span> <span data-ttu-id="29c79-250">По умолчанию используется значение **$true**.</span><span class="sxs-lookup"><span data-stu-id="29c79-250">The default value is **$true**.</span></span>

```powershell
# Enable the warning message when a file is
# opened in multiple PowerShell tabs.
$psISE.Options.ShowWarningForDuplicateFiles = $true
```

### <a name="tokencolors"></a><span data-ttu-id="29c79-251">TokenColors</span><span class="sxs-lookup"><span data-stu-id="29c79-251">TokenColors</span></span>

<span data-ttu-id="29c79-252">Поддерживается в интегрированной среде сценариев Windows PowerShell 2.0 и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="29c79-252">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="29c79-253">Задает цвета маркеров IntelliSense в области сценариев интегрированной среды сценариев Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="29c79-253">Specifies the colors of the IntelliSense tokens in the Windows PowerShell ISE Script pane.</span></span> <span data-ttu-id="29c79-254">Это свойство является объектом словаря, который содержит пары "имя — значение" для типов и цветов маркеров для области сценариев.</span><span class="sxs-lookup"><span data-stu-id="29c79-254">This property is a dictionary object that contains name/value pairs of token types and colors for the Script pane.</span></span> <span data-ttu-id="29c79-255">Сведения об изменении цветов маркеров IntelliSense в области консоли см. в разделе [ConsoleTokenColors](#consoletokencolors).</span><span class="sxs-lookup"><span data-stu-id="29c79-255">To change the colors of the IntelliSense tokens in the Console pane, see [ConsoleTokenColors](#consoletokencolors).</span></span> <span data-ttu-id="29c79-256">Сведения о восстановлении значений по умолчанию для цветов см. в разделе [RestoreDefaultTokenColors](#restoredefaulttokencolors).</span><span class="sxs-lookup"><span data-stu-id="29c79-256">To reset the colors to the default values, see [RestoreDefaultTokenColors](#restoredefaulttokencolors).</span></span> <span data-ttu-id="29c79-257">Можно задать цвета маркера в следующих целях: Атрибут, команды, CommandArgument, CommandParameter, комментарий, GroupEnd, GroupStart, ключевое слово, LineContinuation, LoopLabel, член, символ новой строки, номер, оператор, положение, StatementSeparator, строки, тип, Unknown, переменной.</span><span class="sxs-lookup"><span data-stu-id="29c79-257">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span>

```powershell
# Sets the color of commands to green.
$psISE.Options.TokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.TokenColors["Keyword"] = "magenta"
```

### <a name="useentertoselectinconsolepaneintellisense"></a><span data-ttu-id="29c79-258">UseEnterToSelectInConsolePaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="29c79-258">UseEnterToSelectInConsolePaneIntellisense</span></span>

<span data-ttu-id="29c79-259">Поддерживается в интегрированной среде сценариев Windows PowerShell 3.0 и более поздних версия и отсутствует в более ранних версиях.</span><span class="sxs-lookup"><span data-stu-id="29c79-259">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="29c79-260">Указывает, можно ли использовать клавишу ВВОД для выбора варианта, предложенного IntelliSense, в области консоли.</span><span class="sxs-lookup"><span data-stu-id="29c79-260">Specifies whether you can use the Enter key to select an IntelliSense provided option in the Console pane.</span></span> <span data-ttu-id="29c79-261">По умолчанию используется значение **$true**.</span><span class="sxs-lookup"><span data-stu-id="29c79-261">The default value is **$true**.</span></span>

```powershell
# Turn off using the ENTER key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense = $false
```

### <a name="useentertoselectinscriptpaneintellisense"></a><span data-ttu-id="29c79-262">UseEnterToSelectInScriptPaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="29c79-262">UseEnterToSelectInScriptPaneIntellisense</span></span>

<span data-ttu-id="29c79-263">Поддерживается в интегрированной среде сценариев Windows PowerShell 3.0 и более поздних версия и отсутствует в более ранних версиях.</span><span class="sxs-lookup"><span data-stu-id="29c79-263">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="29c79-264">Указывает, можно ли использовать клавишу ВВОД для выбора варианта, предложенного IntelliSense, в области сценариев.</span><span class="sxs-lookup"><span data-stu-id="29c79-264">Specifies whether you can use the Enter key to select an IntelliSense-provided option in the Script pane.</span></span> <span data-ttu-id="29c79-265">По умолчанию используется значение **$true**.</span><span class="sxs-lookup"><span data-stu-id="29c79-265">The default value is **$true**.</span></span>

```powershell
# Turn on using the Enter key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense = $true
```

### <a name="uselocalhelp"></a><span data-ttu-id="29c79-266">UseLocalHelp</span><span class="sxs-lookup"><span data-stu-id="29c79-266">UseLocalHelp</span></span>

<span data-ttu-id="29c79-267">Поддерживается в интегрированной среде сценариев Windows PowerShell 3.0 и более поздних версия и отсутствует в более ранних версиях.</span><span class="sxs-lookup"><span data-stu-id="29c79-267">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="29c79-268">Указывает, выводится ли на экран локальная справка или справка библиотеки TechNet в Интернете при нажатии клавиши F1, когда курсор находится в ключевом слове.</span><span class="sxs-lookup"><span data-stu-id="29c79-268">Specifies whether the locally installed Help or the online TechNet Library Help appears when you press F1 with the cursor positioned in a keyword.</span></span> <span data-ttu-id="29c79-269">Если задано значение **$true**, во всплывающем окне отображается содержимое локальной справки.</span><span class="sxs-lookup"><span data-stu-id="29c79-269">If set to **$true**, then a pop-up window shows content from the locally installed Help.</span></span> <span data-ttu-id="29c79-270">Можно установить файлы справки, выполнив команду `Update-Help`.</span><span class="sxs-lookup"><span data-stu-id="29c79-270">You can install the Help files by running the `Update-Help` command.</span></span> <span data-ttu-id="29c79-271">Если задано значение **$false**, в браузере открывается страница библиотеки TechNet.</span><span class="sxs-lookup"><span data-stu-id="29c79-271">If set to **$false**, then your browser opens to a page in the TechNet Library.</span></span>

```powershell
# Sets the option for the online help to be displayed.
$psISE.Options.UseLocalHelp = $false
# Sets the option for the local Help to be displayed.
$psISE.Options.UseLocalHelp = $true
```

### <a name="verbosebackgroundcolor"></a><span data-ttu-id="29c79-272">VerboseBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="29c79-272">VerboseBackgroundColor</span></span>

<span data-ttu-id="29c79-273">Поддерживается в интегрированной среде сценариев Windows PowerShell 2.0 и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="29c79-273">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="29c79-274">Задает цвет фона для подробных сообщений, отображаемых в области консоли.</span><span class="sxs-lookup"><span data-stu-id="29c79-274">Specifies the background color for verbose text that appears in the Console pane.</span></span> <span data-ttu-id="29c79-275">Это объект **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="29c79-275">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the background color for verbose text to blue.
$psISE.Options.VerboseBackgroundColor ='#0000FF'
```

### <a name="verboseforegroundcolor"></a><span data-ttu-id="29c79-276">VerboseForegroundColor</span><span class="sxs-lookup"><span data-stu-id="29c79-276">VerboseForegroundColor</span></span>

<span data-ttu-id="29c79-277">Поддерживается в интегрированной среде сценариев Windows PowerShell 2.0 и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="29c79-277">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="29c79-278">Задает цвет переднего плана для подробных сообщений, отображаемых в области консоли.</span><span class="sxs-lookup"><span data-stu-id="29c79-278">Specifies the foreground color for verbose text that appears in the Console pane.</span></span> <span data-ttu-id="29c79-279">Это объект **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="29c79-279">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the foreground color for verbose text to yellow.
$psISE.Options.VerboseForegroundColor = 'yellow'
```

### <a name="warningbackgroundcolor"></a><span data-ttu-id="29c79-280">WarningBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="29c79-280">WarningBackgroundColor</span></span>

<span data-ttu-id="29c79-281">Поддерживается в интегрированной среде сценариев Windows PowerShell 2.0 и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="29c79-281">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="29c79-282">Задает цвет фона для текста предупреждений, отображаемых в области консоли.</span><span class="sxs-lookup"><span data-stu-id="29c79-282">Specifies the background color for warning text that appears in the Console pane.</span></span> <span data-ttu-id="29c79-283">Это объект **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="29c79-283">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the background color for warning text to blue.
$psISE.Options.WarningBackgroundColor = '#0000FF'
```

### <a name="warningforegroundcolor"></a><span data-ttu-id="29c79-284">WarningForegroundColor</span><span class="sxs-lookup"><span data-stu-id="29c79-284">WarningForegroundColor</span></span>

<span data-ttu-id="29c79-285">Поддерживается в интегрированной среде сценариев Windows PowerShell 2.0 и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="29c79-285">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="29c79-286">Задает цвет переднего плана для текста предупреждений, отображаемых в области вывода.</span><span class="sxs-lookup"><span data-stu-id="29c79-286">Specifies the foreground color for warning text that appears in the Output pane.</span></span> <span data-ttu-id="29c79-287">Это объект **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="29c79-287">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the foreground color for warning text to yellow.
$psISE.Options.WarningForegroundColor = 'yellow'
```

### <a name="xmltokencolors"></a><span data-ttu-id="29c79-288">XmlTokenColors</span><span class="sxs-lookup"><span data-stu-id="29c79-288">XmlTokenColors</span></span>

<span data-ttu-id="29c79-289">Поддерживается в интегрированной среде сценариев Windows PowerShell 3.0 и более поздних версия и отсутствует в более ранних версиях.</span><span class="sxs-lookup"><span data-stu-id="29c79-289">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="29c79-290">Указывает объект словаря, который содержит пары "имя — значение" для типов и цветов маркеров для XML-содержимого, которое отображается в интегрированной среде сценариев Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="29c79-290">Specifies a dictionary object that contains name/value pairs of token types and colors for XML content that is displayed in Windows PowerShell ISE.</span></span> <span data-ttu-id="29c79-291">Можно задать цвета маркера в следующих целях: Атрибут, команды, CommandArgument, CommandParameter, комментарий, GroupEnd, GroupStart, ключевое слово, LineContinuation, LoopLabel, член, символ новой строки, номер, оператор, положение, StatementSeparator, строки, тип, Unknown, переменной.</span><span class="sxs-lookup"><span data-stu-id="29c79-291">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span> <span data-ttu-id="29c79-292">См. также [RestoreDefaultXmlTokenColors](#restoredefaultxmltokencolors).</span><span class="sxs-lookup"><span data-stu-id="29c79-292">Also see [RestoreDefaultXmlTokenColors](#restoredefaultxmltokencolors).</span></span>

```powershell
# Sets the color of XML element names to green.
$psISE.Options.XmlTokenColors["ElementName"] = 'green'
# Sets the color of XML comments to magenta.
$psISE.Options.XmlTokenColors["Comment"] = 'magenta'
```

### <a name="zoom"></a><span data-ttu-id="29c79-293">Масштабирование</span><span class="sxs-lookup"><span data-stu-id="29c79-293">Zoom</span></span>

<span data-ttu-id="29c79-294">Поддерживается в интегрированной среде сценариев Windows PowerShell 3.0 и более поздних версия и отсутствует в более ранних версиях.</span><span class="sxs-lookup"><span data-stu-id="29c79-294">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="29c79-295">Указывает относительный размер текста в области консоли и сценариев.</span><span class="sxs-lookup"><span data-stu-id="29c79-295">Specifies the relative size of text in both the Console and Script panes.</span></span> <span data-ttu-id="29c79-296">Значение по умолчанию — 100.</span><span class="sxs-lookup"><span data-stu-id="29c79-296">The default value is 100.</span></span> <span data-ttu-id="29c79-297">Чем больше это значение, тем больше размер отображаемого текста в интегрированной среде сценариев Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="29c79-297">Smaller values cause the text in Windows PowerShell ISE to appear smaller while larger numbers cause text to appear larger.</span></span> <span data-ttu-id="29c79-298">Значение представлено целым числом в диапазоне от 20 до 400.</span><span class="sxs-lookup"><span data-stu-id="29c79-298">The value is an integer that ranges from 20 to 400.</span></span>

```powershell
# Changes the text in the Windows PowerShell ISE to be double its normal size.
$psISE.Options.Zoom = 200
```

## <a name="see-also"></a><span data-ttu-id="29c79-299">См. также</span><span class="sxs-lookup"><span data-stu-id="29c79-299">See Also</span></span>

- [<span data-ttu-id="29c79-300">Назначение объектной модели скриптов интегрированной среды скриптов Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="29c79-300">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="29c79-301">Иерархия объектной модели интегрированной среды скриптов</span><span class="sxs-lookup"><span data-stu-id="29c79-301">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)