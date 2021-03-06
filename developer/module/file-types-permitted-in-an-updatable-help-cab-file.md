---
title: Типы файлов, допустимые в обновляемый файл CAB-файла справки | Документация Майкрософт
ms.custom: ''
ms.date: 03/22/2012
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Windows PowerShell 3.0
ms.assetid: acabdb93-c41a-4b8d-acbe-45cdab91e198
caps.latest.revision: 10
ms.openlocfilehash: 3562804157ebdfca561445a8671d726b55cc4efd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082453"
---
# <a name="file-types-permitted-in-an-updatable-help-cab-file"></a>Типы файлов, которые могут использоваться в CAB-файле обновляемой справки

В этом разделе перечислены и описаны требований к содержимому для обновляемой справки CAB-файлов.

## <a name="updatable-help-cab-file-requirements"></a>Требования к CAB-файл обновляемой справки

По умолчанию несжатого содержимого файла CAB-файлов ограничен 1 ГБ. Чтобы обойти это ограничение, пользователи должны использовать **Force** параметр [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) и [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) командлетов.

Чтобы обеспечить безопасность файлов справки, загруженных из Интернета, обновляемой справки CAB-файл можно включить только типы файлов, перечисленных ниже. [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) командлет проверяет все файлы по схемам раздела справки. Если `Update-Help` командлет обнаружил файл, который является недопустимым или не является типом разрешенных, он не устанавливает недопустимый файл и останавливает установке файлов из CAB-файла на компьютере пользователя.

- Основанный на XML разделы справки по командлетам.

- Основанный на XML разделы справки по сценариям и функциям.

- Основанный на XML разделы справки по поставщикам Windows PowerShell.

- Текстовый разделы справки, таких как разделы справки по модулю.

[Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) проверяет содержимое CAB-файла, когда он распаковывает CAB. Если `Update-Help` находит файл несовместимые типы в обновляемой справки CAB-файл, он создает неустранимую ошибку и останавливает операцию. Он не устанавливает файлы справки из CAB-файла, даже те файл, совместимый типов.