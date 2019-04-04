---
title: Как добавить синтаксис для раздела справки командлета | Документация Майкрософт
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0c6d03f-1c1a-43d8-928e-e3290e90e0bc
caps.latest.revision: 5
ms.openlocfilehash: 2e9dbc9ff8f9507f2008cd6e114ba6fec36b10bf
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054617"
---
# <a name="how-to-add-syntax-to-a-cmdlet-help-topic"></a>Как добавить синтаксис в раздел справки для командлета

- [Атрибуты параметра](#Parameter-Attributes)

- [Атрибуты значение параметра](#Parameter-Value-Attributes)

- [Сбор сведений о синтаксисе](#Gathering-Syntax-Information)

- [Кодирование на схеме синтаксиса XML](#Coding-the-Syntax-Diagram-XML)

## <a name="things-to-know-about-the-syntax-diagram-in-cmdlet-help"></a>Что нужно знать о диаграмма синтаксиса в справку по командлетам

Перед началом кода XML для диаграмма синтаксиса в файле справки командлета, ознакомьтесь с этим разделом, чтобы получить четкое представление о какие данные необходимо предоставить, такую как атрибуты параметров и отображения этих данных на схеме синтаксиса...

### <a name="parameter-attributes"></a>Атрибуты параметра

- Обязательный

  - Если значение равно true, параметр должен указываться во всех командах, использующих набор параметров.

  - Если значение равно false, то параметр является необязательным во всех командах, использующих набор параметров.

- положение

  - Если с именем, имя параметра не требуется.

  - Если позиционные, имя параметра является необязательным. Если опущено, значение параметра должно быть в указанной позиции в команде. Например, если значение равно позиции = «1», значение параметра должен быть первый или только неименованные значение параметра в команде.

- Входные данные конвейера

  - Если значение равно true (ByValue), можно передать по конвейеру входные данные для параметра. Входные данные, связанные с («граница») даже в том случае, если имя свойства и тип объекта не соответствует ожидаемому типу параметра. Windows PowerShell? компоненты привязки параметра попробуйте преобразовать входные данные для правильного типа и завершает команду со сбоем только в том случае, если тип не может быть преобразован. Может быть связан только один параметр в набор параметров по значению.

  - Если значение равно true (ByPropertyName), можно передать по конвейеру входные данные для параметра. Тем не менее входных данных связан с параметром, только в том случае, если имя параметра соответствует имени свойства входного объекта. Например, если имя параметра является `Path`, объекты по конвейеру в командлет связаны с этот параметр только в том случае, если объект имеет свойство с именем пути.

  - Если значение true (ByValue, ByPropertyName), можно передать по конвейеру входные данные для параметра по значению или по имени свойства. Может быть связан только один параметр в набор параметров по значению.

  - Если значение равно false, нельзя передать входные данные для этого параметра.

- Глобализации

  - Если значение равно true, текст, который пользователь вводит для значения параметра может содержать подстановочные знаки.

  - Если значение равно false, текст, который пользователь вводит для значения параметра не может содержать подстановочные знаки.

### <a name="parameter-value-attributes"></a>Атрибуты значение параметра

- Обязательный

  - Значение true, если указанное значение должно использоваться всякий раз, когда с помощью параметра в команде.

  - Если значение равно false, значение параметра является необязательным. Как правило значение является необязательным, только если это одно из нескольких допустимых значений для параметра, например в перечисляемый тип.

Необходимый атрибут значение параметра отличается от обязательный атрибут параметра.

Обязательный атрибут параметра указывает, является ли параметр (и его значение) должен быть включен при вызове командлета. Напротив необходимый атрибут значение параметра используется только в том случае, если параметр включен в команду. Он указывает, следует ли использовать с параметром, определенное значение.

Как правило значения параметров, которые представляют собой заполнители являются обязательными, и значения параметров, которые являются литералами не требуются, так как они являются одной из нескольких значений, которые могут использоваться с параметром.

### <a name="gathering-syntax-information"></a>Сбор сведений о синтаксисе

1. Начинается с имени командлета.

   ```
   SYNTAX
       Get-Tech
   ```

2. Перечислите все параметры командлета. Введите тире (также известная как «тире» или «минус» (ASCII 45) перед именем параметра. Параметры разделения на наборы параметров (в некоторых командлетов может иметь только один набор параметров). В этом примере Get-Технический командлет имеет два набора параметров.

   ```
   SYNTAX
       Get-Tech -name -type
       Get-Tech -ID -list -type
   ```

   Запуск каждого параметра набор с именем командлета.

   Этот параметр по умолчанию, сначала задать в список. Этот параметр по умолчанию указан в классе командлета.

   Для каждого набора параметров список ее уникальный параметр во-первых, только при наличии позиционные параметры, которые должно быть первым. В предыдущем примере, имя и идентификатор равны уникальные параметры для двух наборов параметров (каждый набор параметров должен иметь один параметр, который уникален в этот набор параметров). Это упрощает для пользователей определить, какой параметр, им нужно указать для параметра значение.

   Вывести список параметров в порядке, в котором они должны располагаться в команде. Если порядок не имеет значения, перечислены параметры, связанные друг с другом, или сначала перечислите наиболее часто используемые параметры.

   Убедитесь, что перечислены параметры WhatIf и Confirm в том случае, если командлет поддерживает метод ShouldProcess.

   Не указывайте Общие параметры (например, Verbose, Debug и ErrorAction) в схеме синтаксиса. `Get-Help` Командлет добавляет эту информацию для вас, когда он отображает раздел справки.

3. Добавьте значения параметров. В Windows PowerShell?, значения параметров, представлены по типу .NET. Тем не менее имя типа можно сократить, такие как «string» для System.String.

   ```
   SYNTAX
       Get-Tech -name string -type basic advanced
       Get-Tech -ID int -list -type basic advanced
   ```

   Использование вместо типов до тех пор, пока их значение становится ясно, такие как «string» для System.String и «int» для System.Int32.

   Список всех значений перечисления, таких как параметр - тип в предыдущий пример, в котором можно установить значение «базовый» или «расширенный».

   Переключение параметров, таких как - список в предыдущем примере, не имеют значений.

4. Добавьте значения параметров, которые являются заполнитель, по сравнению с значения параметров, которые являются литералами угловые скобки.

   ```
   SYNTAX
       Get-Tech -name <string> -type basic advanced
       Get-Tech -ID <int> -list -type basic advanced
   ```

5. Заключите необязательные параметры и их значения в квадратных скобках.

   ```
   SYNTAX
       Get-Tech -name <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

6. Имена необязательных параметров (для позиционных параметров), следует заключайте в квадратные скобки. Имя для параметров, которые являются позиционными, такие как имя параметра в следующем примере, нет необходимости включается в команду.

   ```
   SYNTAX
       Get-Tech [-name] <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

7. Если значение параметра может содержать несколько значений, таких как список имен в параметре Name, добавьте пару квадратных скобках непосредственно после значения параметра.

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type basic advanced]
       Get-Tech -ID <int[]> [-list] [-type basic advanced]
   ```

8. Если пользователь может выбрать из параметров или значений параметров, таких как параметр типа, заключите варианты в фигурные скобки, разделив их эксклюзивное symbol(;) OR.

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

9. Если значение параметра необходимо использовать определенное форматирование, например двойных кавычек или фигурных скобок, представления формата в синтаксисе.

   ```
   SYNTAX
       Get-Tech [-name] <"string[]"> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

## <a name="coding-the-syntax-diagram-xml"></a>Кодирование на схеме синтаксиса XML

Узел синтаксиса XML-начинается сразу после описания узла, который заканчивается \</maml:description > тег. Сведения о сборе данных, используемых на схеме синтаксиса см. в разделе [собирать сведения о синтаксисе](#Gathering-Syntax-Information).

### <a name="adding-a-syntax-node"></a>Добавление узла синтаксиса

На схеме синтаксиса, отображаются в разделах справки создается на основе данных в узле синтаксис XML. Узел синтаксиса заключается в пару, если \<синтаксис команды: > теги. С каждым набором параметров командлета, заключенный в паре \<команда: syntaxitem > теги. Нет ограничений на число \<команда: syntaxitem > теги, которые могут быть добавлены.

В следующем примере показано синтаксис узел, содержащий синтаксические узлы элемента для двух наборов параметров.

```xml
<command:syntax>
  <command:syntaxItem>
    ...
    <!--Parameter Set 1 (default parameter set) parameters go here-->
    ...
  </command:syntaxItem>
  <command:syntaxItem>
    ...
    <!--Parameter Set 2 parameters go here-->
    ...
  </command:syntaxItem>
</command:syntax>
```

### <a name="adding-the-cmdlet-name-to-the-parameter-set-data"></a>Добавление имени командлета в параметре набор данных

Каждый набор параметров командлета указывается в узле элемента синтаксиса. Каждый узел синтаксиса элемента начинается с пары \<maml:name > теги, которые включают это имя командлета.

Следующий пример включает синтаксис узел, содержащий синтаксические узлы элемента для двух наборов параметров.

```xml
<command:syntax>
  <command:syntaxItem>
    <maml:name>Cmdlet-Name</maml:name>
  </command:syntaxItem>
  <command:syntaxItem>
    <maml:name>Cmdlet-Name</maml:name>
  </command:syntaxItem>
</command:syntax>
```

### <a name="adding-parameters"></a>Добавление параметров

Каждый параметр, добавляемый узел синтаксического элемента указанного в пару \<: параметр команды > теги. Нужно выделять пару \<: параметр команды > теги для каждого параметра, включенные в набор параметров, за исключением Общие параметры, предоставляемые Windows PowerShell?

Атрибуты открывающего \<: параметр команды > тег определяют, как параметр появляется на схеме синтаксиса. Сведения об атрибутах параметров, см. в разделе [атрибуты параметра](#Parameter-Attributes).

> [!NOTE]
> \<: Параметр команды > тег поддерживает дочерний элемент \<maml:description >, содержимое которых никогда не отображается. Описания параметров указываются в узле параметра XML. Чтобы избежать несогласованности между данными в синтаксис элемента проект и узел параметра, опустите (\<maml:description > или оставьте его пустым.

Следующий пример включает узел элемента синтаксиса для параметров с двумя параметрами.

```xml
<command:syntaxItem>
  <maml:name>Cmdlet-Name</maml:name>
  <command:parameter required="true" globbing="true"
    pipelineInput="true (ByValue)" position="1">
    <maml:name>ParameterName1</maml:name>
    <command:parameterValue required="true">
      string[]
    </command:parameterValue>
  </command:parameter>
  <command:parameter required="true" globbing="true"
    pipelineInput="true (ByPropertyName)">
    <maml:name>ParameterName2</maml:name>
    <command:parameterValue required="true">
      int32[]
    </command:parameterValue>
  </command:parameter>
</command:syntaxItem>
```