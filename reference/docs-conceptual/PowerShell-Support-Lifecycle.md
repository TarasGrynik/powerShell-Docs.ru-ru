---
title: Жизненный цикл поддержки PowerShell Core
description: Политики, распространяемые на поддержку PowerShell Core
ms.date: 08/06/2018
ms.openlocfilehash: b8dd4891ecf245b87c3fe2fa61cd241a12209b57
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854381"
---
# <a name="powershell-core-support-lifecycle"></a>Жизненный цикл поддержки PowerShell Core

PowerShell Core — это отдельный набор средств и компонентов, поставляемых, устанавливаемых и настраиваемых отдельно от Windows PowerShell.
Поэтому на PowerShell Core не распространяются лицензионные соглашения Windows 7, 8.1, 10 или Windows Server.

Однако PowerShell Core поддерживается в рамках традиционных соглашений о поддержке корпорации Майкрософт, включая [Premier][], [Microsoft Enterprise Agreements][enterprise-agreement] и [Microsoft Software Assurance][assurance].
Вы также можете оплатить [техническую поддержку][] по PowerShell Core, направив в службу поддержки запрос о своей проблеме.

## <a name="community-support"></a>Поддержка сообщества

Мы также предлагаем [поддержку сообщества][] на GitHub, где вы можете зарегистрировать вопрос, ошибку или запрос функции.
Кроме того, вы можете обратиться за помощью к другим членам сообщества на сайтах [Microsoft Community][] или Microsoft [PowerShell Tech Community][].
Но мы не можем гарантировать, что там вам оперативно помогут решить вашу проблему.
Если ваша проблема требует немедленного вмешательства, следует использовать традиционные платные варианты поддержки.

## <a name="lifecycle-of-powershell-core"></a>Жизненный цикл PowerShell Core

В PowerShell Core внедряется [политика современного жизненного цикла Майкрософт][modern].
Этот жизненный цикл поддержки предназначен для предоставления клиентам актуальных версий.

Ветвь PowerShell Core версии 6.x будет обновляться примерно каждые шесть месяцев: 6.0, 6.1, 6.2 и т. д.

> [!IMPORTANT]
> Чтобы продолжить получать поддержку, вам нужно обновить продукт в течение шести месяцев после выпуска версии с новым дополнительным номером.

Например, если версия PowerShell Core 6.1 выпущена 1 июля 2018 г., чтобы продолжать получать поддержку, вам нужно выполнить обновление до версии PowerShell Core 6.1 к 1 января 2019 г.

> [!IMPORTANT]
> Кроме того, вам нужно обновлять продукт в течение 30 дней после выпуска версии с новым исправлением.

Например, если вы используете PowerShell Core 6.1, а версия 6.1.3 выпущена 19 февраля 2019 г., вам нужно выполнить обновление до версии PowerShell Core 6.1.3 в течение 30 дней, т. е. до 21 марта 2019 г.
Если требуется какие-либо исправления, они будут включены в наше следующе накопительное обновление.

Согласно политике современного жизненного цикла также требуется, чтобы корпорация Майкрософт предоставляла клиентам уведомление за 12 месяцев до прекращения поддержки продукта (например, PowerShell Core).

Со временем мы планируем реализовать для PowerShell Core возможность долгосрочного обслуживания.
Это позволит нам осуществлять обслуживание и выпускать обновления для системы безопасности, чтобы обеспечить поддержку определенной ветви или версии 6.x.

## <a name="supported-platforms"></a>Поддерживаемые платформы

В таблице ниже указано, какая платформа используемой версии PowerShell Core официально поддерживается.

Наше сообщество также предоставило пакеты для некоторых платформ, но они не поддерживаются официально.
Эти пакеты, отмечены как `Community` в таблице.

Отмеченные как `Experimental` платформы официально не поддерживаются, но доступны для экспериментов с возможностью обратной связи.

|                                                   | 6.1         | 6.2         |
|---------------------------------------------------|:-----------:|:-----------:|
| Windows 7, 8.1 и 10                            | Поддерживается   | Поддерживается   |
| Windows Server 2008 R2, 2012 R2, 2016             | Поддерживается   | Поддерживается   |
| [Windows Server Semi-Annual Channel][semi-annual] | Поддерживается   | Поддерживается   |
| Ubuntu 16.04 и 18.04                            | Поддерживается   | Поддерживается   |
| Ubuntu 18.10 (с помощью snap-пакета)                   | Сообщество   | Сообщество   |
| Debian 9                                          | Поддерживается   | Поддерживается   |
| CentOS 7                                          | Поддерживается   | Поддерживается   |
| Red Hat Enterprise Linux 7                        | Поддерживается   | Поддерживается   |
| openSUSE 42.3                                     | Поддерживается   | Поддерживается   |
| Fedora 28                                         | Поддерживается   | Поддерживается   |
| macOS 10.12+                                      | Поддерживается   | Поддерживается   |
| Arch                                              | Сообщество   | Сообщество   |
| Raspbian                                          | Сообщество   | Сообщество   |
| Kali                                              | Сообщество   | Сообщество   |
| AppImage (работает на нескольких платформах Linux)     | Сообщество   | Сообщество   |
| [Snap-пакет](https://snapcraft.io/powershell)   | См. примечание    | См. примечание    |

> [!NOTE]
> Прикрепленные пакеты поддерживаются так же, как и соответствующий дистрибутив.

## <a name="powershell-release-end-of-life"></a>Завершение жизненного цикла PowerShell

В следующей таблице перечислены даты прекращения поддержки разных выпусков PowerShell Core с учетом [жизненного цикла этого продукта](#lifecycle-of-powershell-core).

| Версия | Завершение срока службы                   |
|---------|-------------------------------|
| 6.0     | 13 февраля 2019 г.             |
| 6.1     | 28 сентября 2019 г.            |
| 6.2     | 6 месяцев после выпуска версии 7     |

## <a name="platforms-which-are-out-of-support"></a>Неподдерживаемые платформы

По завершении жизненного цикла определенной версии платформы (определяется ее владельцем), прекращается ее поддержка в PowerShell Core.
Предыдущие выпуски пакетов останутся доступными для клиентов, которым требуется доступ, но официальная поддержка и обновления больше не будет предоставляться.

Таким образом, поддержка следующих версий прекращается владельцами дистрибутивов.

| ОС       | Версия | Завершение срока службы                                                                                 |
|----------|---------|---------------------------------------------------------------------------------------------|
| Fedora   | 24      | [Август 2017 г.](https://fedoramagazine.org/fedora-24-eol/)                                    |
| Fedora   | 25      | [Декабрь 2017 г.](https://fedoramagazine.org/fedora-25-end-life/)                             |
| Fedora   | 26      | [Май 2018 г.](https://fedoramagazine.org/fedora-26-end-life/)                                  |
| openSUSE | 42.1    | [Май 2017 г.](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)     |
| openSUSE | 42.2    | [Январь 2018 г.](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html) |
| Ubuntu   | 16.10   | [Июль 2017 г.](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)        |
| Ubuntu   | 17.04   | [Январь 2018 г.](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)          |
| Ubuntu   | 17.10   | [Июль 2018 г.](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)        |
| Debian   | 8       | [Июнь 2018 г.](https://lists.debian.org/debian-security-announce/2018/msg00132.html)           |
| Fedora   | 27      | [Ноябрь 2018 г.](https://fedoramagazine.org/fedora-27-end-of-life/)                          |
| Ubuntu   | 14.04   | [Апрель 2019 г.](https://wiki.ubuntu.com/Releases)                                              |

## <a name="notes-on-licensing"></a>Замечания по лицензированию

PowerShell Core выпускается по [Лицензия MIT][].
По этой лицензии и без соглашения о платной подписке пользователям предоставляется только [поддержку сообщества][].
В рамках поддержки сообщества корпорация Майкрософт не предоставляет никаких гарантий оперативного реагирования или выпуска исправлений.

## <a name="windows-powershell-module"></a>Модуль Windows PowerShell

Поддержка PowerShell Core не распространяется на другие модули продукта, если только они не поддерживают PowerShell Core явным образом.
Например, использование модуля `ActiveDirectory`, который поставляется в составе Windows Server, является неподдерживаемым сценарием.

Однако в некоторых случаях модули, которые не поддерживают PowerShell Core явным образом, могут быть совместимы.
Установив модуль [`WindowsPSModulePath`][], можно добавить `PSModulePath` Windows PowerShell в `PSModulePath` PowerShell Core.

Сначала установите модуль `WindowsPSModulePath` из коллекции PowerShell:

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

После установки модуля запустите командлет `Add-WindowsPSModulePath`, чтобы добавить `PSModulePath` Windows PowerShell в PowerShell Core:

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

## <a name="experimental-features"></a>Экспериментальные функции

Для [Экспериментальные функции][] предоставляется только [поддержка сообщества](#community-support).

[Premier]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
[enterprise-agreement]: https://www.microsoft.com/en-us/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/en-us/licensing/licensing-programs/software-assurance-default.aspx
[поддержку сообщества]: https://github.com/powershell/powershell/issues
[Microsoft Community]: https://answers.microsoft.com/
[PowerShell Tech Community]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[техническую поддержку]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
[Лицензия MIT]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
["WindowsPSModulePath"]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[Экспериментальные функции]: /powershell/module/microsoft.powershell.core/about/about_powershell_config?view=powershell-6#experimentalfeatures
