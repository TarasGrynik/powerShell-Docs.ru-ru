---
title: Основные сведения о кодировке файлов в VSCode и PowerShell
description: Настройка кодировки файлов в VSCode и PowerShell
ms.date: 02/28/2019
ms.openlocfilehash: ec06d8f5d446a92e6cd9d2d70b11260d1d0afda8
ms.sourcegitcommit: 396509cd0d415acc306b68758b6f833406e26bf5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/21/2019
ms.locfileid: "58320410"
---
# <a name="understanding-file-encoding-in-vscode-and-powershell"></a>Основные сведения о кодировке файлов в VSCode и PowerShell

При использовании VS Code для создания и редактирования сценариев PowerShell очень важно, чтобы ваши файлы сохранялись в правильной кодировке символов.

## <a name="what-is-file-encoding-and-why-is-it-important"></a>Что такое кодировка и почему она важна?

VSCode управляет интерфейсом между человеком, вводящим строки символов в буфер, и чтением-записью блоков байтов в файловой системе. Когда VSCode сохраняет файл, используется кодировка текста.

Аналогичным образом, когда оболочка PowerShell запускает скрипт, ей необходимо преобразовать байты из файла в символы для преобразования файла в программу PowerShell. Поскольку VSCode записывает файл, а PowerShell считывает файл, им необходимо использовать одну и ту же систему кодировки. Этот процесс синтаксического анализа скрипта PowerShell идет так: *байты* -> *символы* -> *лексемы* ->  *дерево абстрактного синтаксиса* -> *выполнение*.

И VSCode, и PowerShell устанавливаются с подходящей конфигурацией кодировки по умолчанию. Тем не менее кодировка по умолчанию, используемая PowerShell, была изменена с выпуском PowerShell Core (версии 6.x). Чтобы избежать проблем с PowerShell или расширениями PowerShell в VSCode, необходимо настроить параметры VSCode и PowerShell должным образом.

## <a name="common-causes-of-encoding-issues"></a>Распространенные причины проблемы с кодировкой

Проблемы с кодировкой возникают, если кодировка VSCode в целом или вашего файла скрипта не совпадает с ожидаемой кодировкой PowerShell. В PowerShell нет способа автоматически определить кодировку файла.

Проблемы с кодировкой более вероятны при использовании символов не из [7-разрядной кодировки ASCII](https://ascii.cl/). Например:

- Латинские символы с диакритикой (`É`, `ü`)
- Нелатинские символы, такие как кириллица (`Д`, `Ц`)
- Китайская письменность ханьцзы (`脚`, `本`)

Распространенные причины проблем с кодировкой:

- Настройки кодировок по умолчанию VSCode и PowerShell не были изменены. В PowerShell 5.1 и ниже кодировка по умолчанию отличается от используемой в VSCode.
- Открыт другой редактор, и файл перезаписан в новой кодировке. Это часто происходит с интегрированной средой сценариев.
- Файл возвращается в систему управления версиями в кодировке, отличной от той, что ожидает VSCode или PowerShell. Это может произойти, когда участники совместной работы используют редакторы с различными конфигурациями кодировок.

### <a name="how-to-tell-when-you-have-encoding-issues"></a>Как определить наличие проблемы с кодировкой

Часто ошибки кодирования в скриптах представляются как ошибки синтаксического анализа. Если вы видите странные последовательности символов в скрипте, это может быть проблемой. В примере ниже тире (`–`) отображается в виде символов `â€“`:

```Output
Send-MailMessage : A positional parameter cannot be found that accepts argument 'Testing FuseMail SMTP...'.
At C:\Users\<User>\<OneDrive>\Development\PowerShell\Scripts\Send-EmailUsingSmtpRelay.ps1:6 char:1
+ Send-MailMessage â€“From $from â€“To $recipient1 â€“Subject $subject  ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Send-MailMessage], ParameterBindingException
    + FullyQualifiedErrorId : PositionalParameterNotFound,Microsoft.PowerShell.Commands.SendMailMessage
```

Эта проблема возникает, так как VSCode кодирует символ `–` в UTF-8 при помощи байтов `0xE2 0x80 0x93`.
Если эти байты декодируются в кодировке Windows-1252, они интерпретируются как символы `â€“`.

Некоторые странные последовательности символов, которые можно видеть:

<!-- markdownlint-disable MD038 -->
- `â€“` вместо `–`;
- `â€”` вместо `—`;
- `Ã„2` вместо `Ä`;
- `Â` вместо ` ` (неразрывный пробел);
- `Ã©` вместо `é`.
<!-- markdownlint-enable MD038 -->

Этот удобный [справочник](https://www.i18nqa.com/debug/utf8-debug.html) перечисляет распространенные шаблоны, которые указывают на проблему между кодировками UTF-8 и Windows-1252.

## <a name="how-the-powershell-extension-in-vscode-interacts-with-encodings"></a>Взаимодействие расширения PowerShell в VSCode с кодировками

Расширение PowerShell взаимодействует со скриптами несколькими способами:

1. При изменении скриптов в VSCode содержимое отправляются из VSCode в расширение. [Протокол языкового сервера][] требует, чтобы это содержимое передавалось в UTF-8. Таким образом, расширение не сможет получить неправильную кодировку.
2. При выполнении скриптов в интегрированной консоли они считываются оболочкой PowerShell непосредственно из файла. Если кодировка PowerShell отличается от кодировки VSCode, что-нибудь здесь может пойти не так.
3. Когда скрипт, который открыт в VSCode, ссылается на другой скрипт, который не был открыт в VSCode, расширение загружает содержимое второго скрипта из файловой системы. Расширение PowerShell по умолчанию использует кодировку UTF-8, но при этом применяет обнаружение [Метка порядка байтов][] (BOM), чтобы выбрать правильную кодировку.

Проблема возникает при предположении кодировки, не использующей BOM (такой как [UTF-8][] без метки порядка байтов или [Windows-1252][]).
Расширение PowerShell по умолчанию использует UTF-8. Расширение не может изменить параметры кодировки в VSCode.
Дополнительные сведения см. в разделе [Проблема № 824](https://github.com/Microsoft/vscode/issues/824).

## <a name="choosing-the-right-encoding"></a>Выбор подходящей кодировки

Различные системы и приложения могут использовать различные кодировки:

- В .NET Standard, в Интернете и в среде Linux теперь в основном используется кодировка UTF-8.
- Во многих приложениях .NET Framework используется [UTF-16][]. По историческим причинам ее иногда называют "Юникод"; сейчас этот термин относится к более широкому [стандарту](https://en.wikipedia.org/wiki/Unicode), охватывающему UTF-8 и UTF-16.
- В Windows многие приложения, которые были созданы еще до распространения Юникода, по-прежнему могут по умолчанию использовать Windows-1252.

Кодировки Юникода также используют понятие метки порядка следования байтов (BOM). BOM ставится в начале текста, чтобы декодер мог определить, какая кодировка используется в тексте. Для многобайтовых кодировок BOM также указывает [порядок следования байтов](https://en.wikipedia.org/wiki/Endianness) кодировки. BOM представляются байтами, которые редко встречаются в тексте в Юникоде. Это позволяет сделать обоснованное предположение, что текст записан в Юникоде, если присутствует метка BOM.

BOM не являются обязательными; в мире Linux они не так популярны, поскольку во всех прочих местах используется надежное соглашение UTF-8. Большинство приложений Linux предполагают, что текстовый ввод кодируется в UTF-8. Хотя многие приложения Linux могут распознавать и правильно обрабатывать BOM, некоторые этого не делают, что приводит к появлению артефактов в тексте, открываемом с помощью этих приложений.

**Таким образом**:

- Если вы работаете в основном с приложениями Windows и Windows PowerShell, следует предпочтительно использовать такие кодировки, как UTF-8 с BOM или UTF-16.
- Если вы работаете на разных платформах, следует отдавать предпочтение UTF-8 с BOM.
- Если вы работаете главным образом в контексте Linux, следует отдавать предпочтение UTF-8 без BOM.
- Windows-1252 и latin-1 — устаревшие кодировки, которых по возможности следует избегать.
  Тем не менее некоторые приложения предыдущих версий в Windows зависят от их.
- Также стоит отметить, что подписывание скриптов [зависит от кодировки](https://github.com/PowerShell/PowerShell/issues/3466), то есть изменение кодировки в подписанном скрипте потребует повторного подписывания.

## <a name="configuring-vscode"></a>Настройка VSCode

Кодировка VSCode по умолчанию — UTF-8 без метки порядка байтов.

Чтобы задать [Кодировка в VSCode][], перейдите к параметрам VSCode (<kbd>Ctrl<kbd>+</kbd>,</kbd>) и задайте параметр `"files.encoding"`:

```json
"files.encoding": "utf8bom"
```

Возможны следующие значения:

- `utf8`: [UTF-8] без метки порядка байтов
- `utf8bom`: [UTF-8] с меткой порядка байтов
- `utf16le`: [UTF-16] с прямым порядком байтов
- `utf16be`: [UTF-16] с обратным порядком байтов
- `windows1252`: [Windows-1252]

Должен отобразиться раскрывающийся список представления графического пользовательского интерфейса или дополнение в представлении JSON.

Чтобы обеспечить автоматическое определение кодировки, если это возможно, можно также добавить следующее:

```json
"files.autoGuessEncoding": true
```

Если вы не хотите, чтобы эти параметры влияли на все типы файлов, VSCode также позволяет задавать конфигурации для каждого языка отдельно. Создать параметр для конкретного языка можно, поместив параметры в поле `[<language-name>]`. Например:

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

## <a name="configuring-powershell"></a>Настройка PowerShell

В PowerShell кодировка по умолчанию зависит от версии:

- В PowerShell 6+ кодировка по умолчанию на всех платформах — UTF-8 без метки порядка байтов.
- В Windows PowerShell кодировка по умолчанию — обычно Windows-1252, расширение [latin-1][], которое также называется ISO 8859-1.

В PowerShell 5 + можно определить кодировку по умолчанию так:

```powershell
[psobject].Assembly.GetTypes() | Where-Object { $_.Name -eq 'ClrFacade'} |
  ForEach-Object {
    $_.GetMethod('GetDefaultEncoding', [System.Reflection.BindingFlags]'nonpublic,static').Invoke($null, @())
  }
```

Следующий [скрипт](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) может использоваться для определения кодировки, которую ваш сеанс PowerShell выводит для скрипта, где нет метки порядка байтов.

```powershell
$badBytes = [byte[]]@(0xC3, 0x80)
$utf8Str = [System.Text.Encoding]::UTF8.GetString($badBytes)
$bytes = [System.Text.Encoding]::ASCII.GetBytes('Write-Output "') + [byte[]]@(0xC3, 0x80) + [byte[]]@(0x22)
$path = Join-Path ([System.IO.Path]::GetTempPath()) 'encodingtest.ps1'

try
{
    [System.IO.File]::WriteAllBytes($path, $bytes)

    switch (& $path)
    {
        $utf8Str
        {
            return 'UTF-8'
            break
        }

        default
        {
            return 'Windows-1252'
            break
        }
    }
}
finally
{
    Remove-Item $path
}
```

Можно настроить PowerShell так, чтобы использовать заданную кодировку в более общем виде с помощью параметров профиля. См. следующие статьи:

- [Ответ [@mklement0] о кодировке PowerShell на сайте StackOverflow](https://stackoverflow.com/a/40098904).
- [Запись блога [@rkeithhill] об обработке входных данных в UTF-8 без метки порядка байтов в PowerShell](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/).

Заставить PowerShell использовать конкретную кодировку для входных данных невозможно. PowerShell 5.1 и более ранние версии по умолчанию используют кодировку Windows-1252, если отсутствует BOM. По причинам совместимости лучше сохранять скрипты в Юникоде с меткой порядка байтов.

> [!IMPORTANT]
> Любые другие имеющиеся у вас инструменты для работы со скриптами PowerShell могут зависеть от выбранных параметров кодировки или преобразовывать скрипты в другую кодировку.

### <a name="existing-scripts"></a>Существующие скрипты

Скрипты, которые уже находятся в файловой системе, могут нуждаться в повторном кодировании в указанную вами кодировку. В нижней строке VSCode вы увидите метку UTF-8. Щелкните ее, чтобы открыть панель действий, и выберите команду **Сохранить с кодировкой**. Теперь вы можете выбрать новую кодировку для этого файла. См. подробные инструкции в разделе [Кодировка в VSCode][].

Если вам нужно повторно кодировать несколько файлов, можно использовать следующий скрипт:

```powershell
Get-ChildItem *.ps1 -Recurse | ForEach-Object {
    $content = Get-Content -Path $_
    Set-Content -Path $_.Fullname -Value $content -Encoding UTF8 -PassThru -Force
}
```

### <a name="the-powershell-integrated-scripting-environment-ise"></a>Интегрированная среда сценариев (ISE) PowerShell

При редактировании скриптов с помощью интегрированной среды сценариев PowerShell необходимо синхронизировать здесь параметры кодировки.

Интегрированная среда сценариев должна учитывать метку порядка байтов, но можно также использовать отражение для [задания кодировки](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/).
Обратите внимание, что это значение не сохраняется между запусками.

### <a name="source-control-software"></a>Система управления версиями

Некоторые системы управления версиями, например git, игнорируют кодировки; git отслеживает только байты.
Поведение других, например Azure DevOps или Mercurial, может отличаться. Даже некоторые средства, основанные на git, полагаются на декодирование текста.

Если это так, убедитесь, что вы:

- Настроили кодировку в системе управления версиями в соответствии с вашей конфигурацией VSCode.
- Сделали так, что все файлы добавляются в систему управления версиями в соответствующей кодировке.
- Остерегайтесь изменять кодировки, полученные через систему управления версиями. Ключевым признаком здесь будет разностный файл, который указывает, что изменения отсутствуют (так как изменены байты, но не символы).

### <a name="collaborators-environments"></a>Среды других участников

Настроив систему управления версиями, убедитесь также, что параметры других участников, работающих над теми файлами, к которым вы предоставляете общий доступ, не переопределяют кодировку путем повторного кодирования файлов PowerShell.

### <a name="other-programs"></a>Другие программы

Все другие программы, которые считывают или записывают скрипты PowerShell, могут перекодировать их.

Вот несколько примеров.

- Использование буфера обмена для копирования и вставки скрипта. Такое часто встречается в следующих случаях:
  - Копирование скрипта в виртуальную машину.
  - Копирование скрипта из электронной почты или с веб-страницы.
  - Копирование скрипта через документ Microsoft Word или PowerPoint.
- Другие текстовые редакторы, например:
  - Блокнот;
  - vim;
  - любой другой редактор скриптов PowerShell.
- Служебные программы редактирования текста, например:
  - `Get-Content`/`Set-Content`/`Out-File`
  - Операторы перенаправления PowerShell, такие как `>` и `>>`.
  - `sed`/`awk`
- Программы передачи файлов, такие как:
  - Веб-браузер при скачивании скриптов.
  - Общий файловый ресурс.

Некоторые из этих средств работают с байтами, а не с текстом, но другие позволяют настраивать кодировки. В случаях, когда необходимо настроить кодировку, используйте те же параметры, что и в вашем редакторе, чтобы предотвратить возникновение проблем.

## <a name="other-resources-on-encoding-in-powershell"></a>Другие ресурсы о кодировках в PowerShell

Существует несколько других достойных публикаций на тему кодировок и настройки кодирования в PowerShell:

- [Обзор [@mklement0] о кодировке PowerShell на сайте StackOverflow](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8).
- Предыдущие проблемы с кодировками, найденные в vscode-PowerShell:
  - [#1308](https://github.com/PowerShell/vscode-powershell/issues/1308)
  - [#1628](https://github.com/PowerShell/vscode-powershell/issues/1628)
  - [#1680](https://github.com/PowerShell/vscode-powershell/issues/1680)
  - [#1744](https://github.com/PowerShell/vscode-powershell/issues/1744)
  - [#1751](https://github.com/PowerShell/vscode-powershell/issues/1751)
- [Классическая статья *Joel on Software* про Юникод](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)
- [Кодировка в .NET Standard](https://github.com/dotnet/standard/issues/260#issuecomment-289549508)


[@mklement0]: https://github.com/mklement0
[@rkeithhill]: https://github.com/rkeithhill
[Windows-1252]: https://wikipedia.org/wiki/Windows-1252
[latin-1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[UTF-8]: https://wikipedia.org/wiki/UTF-8
[Метка порядка байтов]: https://wikipedia.org/wiki/Byte_order_mark
[UTF-16]: https://wikipedia.org/wiki/UTF-16
[Протокол языкового сервера]: https://microsoft.github.io/language-server-protocol/
[Кодировка в VSCode]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support