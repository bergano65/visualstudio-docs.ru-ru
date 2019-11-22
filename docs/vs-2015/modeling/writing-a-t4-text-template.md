---
title: Writing a T4 Text Template | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, syntax
- text templates, guide
- text templates, functions that generate text
ms.assetid: 94328da7-953b-4e92-9587-648543d1f732
caps.latest.revision: 45
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bcd5a4996db4a5e374baabe4f52d5fd1dbac2e5e
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301122"
---
# <a name="writing-a-t4-text-template"></a>Написание текстового шаблона T4
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Текстовый шаблон содержит текст, который будет создан на его основе. For example, a template that creates a web page will contain "\<html>…" and all the other standard parts of an HTML page. Inserted into the template are *control blocks*, which are fragments of program code. Блоки управления обеспечивают варьирующиеся значения и обеспечивают условность и повторяемость текста.

 Эта структура упрощает разработку шаблона, так как можно начать с прототипа созданного файла и постепенно вставлять блоки управления, которые будут обеспечивать изменение результата.

 Текстовые шаблоны состоят из следующих частей.

- **Directives** - elements that control how the template is processed.

- **Text blocks** - content that is copied directly to the output.

- **Control blocks** - program code that inserts variable values into the text, and controls conditional or repeated parts of the text.

  To try the examples in this topic, copy them into a template file as described in [Design-Time Code Generation by using T4 Text Templates](../modeling/design-time-code-generation-by-using-t4-text-templates.md). After editing the template file, save it, and then inspect the output **.txt** file.

## <a name="directives"></a>Директивы
 Директивы текстовых шаблонов предоставляют общие инструкции модулю текстовых шаблонов в отношении порядка создания кода преобразования и выходного файла.

 Например, следующая директива указывает, что выходной файл должен иметь расширение .TXT.

```

<#@ output extension=".txt" #>
```

 For more information about directives, see [T4 Text Template Directives](../modeling/t4-text-template-directives.md).

## <a name="text-blocks"></a>Текстовые блоки
 Текстовый блок вставляет текст непосредственно в выходной файл. Для текстовых блоков нет особых правил форматирования. Например, следующий текстовый шаблон создаст текстовый файл со словом "Hello":

```
<#@ output extension=".txt" #>
Hello
```

## <a name="control-blocks"></a>Блоки управления
 Блоки управления — это части программного кода, которые используются для преобразования шаблонов. Язык по умолчанию — C#, поэтому для использования [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] можно вставить в начало файла эту директиву:

```
<#@ template language="VB" #>
```

 Язык, на котором вы будете писать код в блоках управления, не связан с языком создаваемого текста.

### <a name="standard-control-blocks"></a>Стандартные блоки управления
 Стандартный блок управления представляет собой раздел программного кода, который создает часть выходного файла.

 В файле шаблона можно смешивать любое число блоков текста и стандартных блоков управления. При этом нельзя помещать один блок управления в другой. Каждый стандартный блок управления отделяется символами `<# ... #>`.

 Например, следующий блок управления и текстовый блок создают выходной файл, который содержит строку "0, 1, 2, 3, 4 Hello!":

```

      <#
    for(int i = 0; i < 4; i++)
    {
        Write(i + ", ");
    }
    Write("4");
#> Hello!
```

 Вместо использования явных операторов `Write()`, можно чередовать текст и код. The following example prints "Hello!" four times:

```
<#
    for(int i = 0; i < 4; i++)
    {
#>
Hello!
<#
    }
#>
```

 Можно вставить блок текста в любое место кода, где допускается вставка оператора `Write();`.

> [!NOTE]
> When you embed a text block within a compound statement such as a loop or conditional, always use braces {...} to contain the text block.

### <a name="expression-control-blocks"></a>Блоки управления выражениями
 Блок управления выражением оценивает выражение и преобразует его в строку, которая вставляется в выходной файл.

 Блоки управления выражениями разделяются символами `<#= ... #>`

 Например, следующий блок управления задает, что выходной файл будет содержать "5":

```
<#= 2 + 3 #>
```

 Notice that the opening symbol has three characters "<#=".

 Это выражение может включать любую переменную в области. Например, этот блок печатает строки цифр:

```
<#@ output extension=".txt" #>
<#
    for(int i = 0; i < 4; i++)
    {
#>
This is hello number <#= i+1 #>: Hello!
<#
    }
#>
```

### <a name="class-feature-control-blocks"></a>Блоки управления возможностями класса
 Блок управления возможностями класса определяет свойства, методы или другой код, который не должен включаться в основное преобразование. Блоки возможностей класса часто используются для написания возможностей вспомогательных приложений.  Typically, class feature blocks are placed in separate files so that they can be [included](#Include) by more than one text template.

 Блоки управления возможностями класса разделяются символами `<#+ ... #>`.

 Например, следующий файл шаблона объявляет и использует метод:

```
<#@ output extension=".txt" #>
Squares:
<#
    for(int i = 0; i < 4; i++)
    {
#>
    The square of <#= i #> is <#= Square(i+1) #>.
<#
    }
#>
That is the end of the list.
<#+   // Start of class feature block
private int Square(int i)
{
    return i*i;
}
#>
```

 Возможности класса необходимо помещать в конец файла, в котором они написаны. Однако можно включить файл (используя `<#@include#>`), содержащий возможность класса, даже если за директивой `include` следует текст и стандартные блоки.

 For more information about control blocks, see [Text Template Control Blocks](../modeling/text-template-control-blocks.md).

### <a name="class-feature-blocks-can-contain-text-blocks"></a>Блоки возможностей класса могут содержать текстовые блоки
 Вы можете написать метод, создающий текст. Пример:

```
List of Squares:
<#
   for(int i = 0; i < 4; i++)
   {  WriteSquareLine(i); }
#>
End of list.
<#+   // Class feature block
private void WriteSquareLine(int i)
{
#>
   The square of <#= i #> is <#= i*i #>.
<#+
}
#>
```

 Особенно полезным будет поместить метод, создающий текст, в отдельный файл, который можно будет включить в несколько шаблонов.

## <a name="using-external-definitions"></a>Использование внешних определений

### <a name="assemblies"></a>Сборки
 Блоки кода шаблона могут использовать типы, определенные в наиболее часто используемых сборках .NET, таких как System.dll. Кроме того, можно добавить ссылку на другие сборки .NET или ваши собственные. Можно предоставить путь или строгое имя сборки:

```
<#@ assembly name="System.Xml" #>
```

 Необходимо использовать абсолютные пути или стандартные имена макросов в пути. Пример:

```
<#@ assembly name="$(SolutionDir)library\MyAssembly.dll" #>
```

 For a list of macros, see [Common Macros for Build Commands and Properties](https://msdn.microsoft.com/library/239bd708-2ea9-4687-b264-043f1febf98b).

 The assembly directive has no effect in a [preprocessed text template](../modeling/run-time-text-generation-with-t4-text-templates.md).

 For more information, see [T4 Assembly Directive](../modeling/t4-assembly-directive.md).

### <a name="namespaces"></a>Пространства имен
 Директива import соответствует выражению `using` в C# или выражению `imports` в Visual Basic. Она позволяет ссылаться на типы в коде, не используя полное имя:

```
<#@ import namespace="System.Xml" #>
```

 Число используемых директив `assembly` и `import` не ограничено. Их нужно размещать до блоков управления и текста.

 For more information, see [T4 Import Directive](../modeling/t4-import-directive.md).

### <a name="Include"></a> Including code and text
 Директива `include` вставляет текст из другого файла шаблона. Например, эта директива вставляет содержимое файла `test.txt`:

 `<#@ include file="c:\test.txt" #>`

 Включенное содержимое обрабатывается почти так же, как если бы оно было частью включающего текстового шаблона. При этом можно включить файл, содержащий блок возможностей класса `<#+...#>`, даже если за директивой include следуют обычный текст и стандартные блоки управления.

 For more information, see [T4 Include Directive](../modeling/t4-include-directive.md).

### <a name="utility-methods"></a>Служебные методы
 Существует несколько методов, таких как `Write()`, которые всегда можно использовать в блоке управления. Они включают методы, помогающие создать отступы для вывода или отчеты об ошибках.

 Кроме того, вы можете создать собственный набор служебных методов.

 For more information, see [Text Template Utility Methods](../modeling/text-template-utility-methods.md).

## <a name="transforming-data-and-models"></a>Преобразование данных и моделей
 Наиболее полезная сфера применения текстовых шаблонов — создание материалов на основе содержимого источника, такого как модель, база данных или файл данных. Шаблон извлекает данные и изменяет их формат. Коллекция шаблонов может преобразовать подобный источник в несколько файлов.

 Существует несколько способов считывания исходного файла.

 **Read a file in the text template**. Это самый простой способ получения данных в шаблоне:

```
<#@ import namespace="System.IO" #>
<# string fileContent = File.ReadAllText(@"C:\myData.txt"); ...
```

 **Load a file as a navigable model**. Более эффективный способ — это чтение данных как модели, по которой может перемещаться код текстового шаблона. Например, можно загрузить XML-файл и выполнять навигацию по этому файлу с помощью выражений XPath. You could also use [xsd.exe](https://go.microsoft.com/fwlink/?LinkId=178765) to create a set of classes with which you can read the XML data.

 **Edit the model file in a diagram or form.** [!INCLUDE[dsl](../includes/dsl-md.md)] provides tools that let you edit a model as a diagram or Windows form. Это упрощает обсуждение модели с пользователями созданного приложения. [!INCLUDE[dsl](../includes/dsl-md.md)] также создает набор строго типизированных классов, отражающих структуру модели. For more information, see [Generating Code from a Domain-Specific Language](../modeling/generating-code-from-a-domain-specific-language.md).

 **Use a UML model**. Можно создать код на основе модели UML. Это обеспечивает преимущество редактирования модели в качестве схемы в рамках привычной нотации. Кроме того, вам не потребуется разрабатывать схему. For more information, see [Generate files from a UML model](../modeling/generate-files-from-a-uml-model.md).

### <a name="relative-file-paths-in-design-time-templates"></a>Относительные пути файлов в шаблонах времени разработки
 In a [design-time text template](../modeling/design-time-code-generation-by-using-t4-text-templates.md), if you want to reference a file in a location relative to the text template, use `this.Host.ResolvePath()`. Кроме того, необходимо задать выражение `hostspecific="true"` в директиве `template`:

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ import namespace="System.IO" #>
<#
 // Find a path within the same project as the text template:
 string myFile = File.ReadAllText(this.Host.ResolvePath("MyFile.txt"));
#>
Content of MyFile.txt is:
<#= myFile #>

```

 Можно также получить другие службы, предоставляемые узлом. For more information, see [Accessing Visual Studio or other Hosts from a Template](https://msdn.microsoft.com/0556f20c-fef4-41a9-9597-53afab4ab9e4).

### <a name="design-time-text-templates-run-in-a-separate-appdomain"></a>Текстовые шаблоны времени разработки выполняются в отдельном домене приложения
 You should be aware that a [design-time text template](../modeling/design-time-code-generation-by-using-t4-text-templates.md) runs in an AppDomain that is separate from the main application. В большинстве случаев это неважно, однако вы можете столкнуться с ограничениями в некоторых сложных случаях. Например, если нужно передать данные в шаблон или из него, используя отдельную службу, эта служба должна предоставить сериализуемый API.

 (This isn’t true of a [run-time text template](../modeling/run-time-text-generation-with-t4-text-templates.md), which provides code that is compiled along with the rest of your code.)

## <a name="editing-templates"></a>Редактирование шаблонов
 Специализированные редакторы текстовых шаблонов можно загрузить из каталога диспетчера расширений в Интернете. On the **Tools** menu, click **Extension Manager**. Click **Online Gallery**, and then use the search tool.

## <a name="related-topics"></a>См. также

|Задача|Раздел|
|----------|-----------|
|Создание шаблона.|[Рекомендации по написанию текстовых шаблонов T4](../modeling/guidelines-for-writing-t4-text-templates.md)|
|Создание текста с помощью программного кода.|[Text Template Structure](../modeling/writing-a-t4-text-template.md)|
|Создание файлов в решении [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|[Создание кода во время разработки с помощью текстовых шаблонов T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|
|Запуск создания текста за пределами [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|[Создание файлов с помощью служебной программы TextTransform](../modeling/generating-files-with-the-texttransform-utility.md)|
|Преобразование данных в форме доменного языка.|[Создание кода из доменного языка](../modeling/generating-code-from-a-domain-specific-language.md)|
|Написание процессоров директив для преобразования собственных источников данных.|[Настройка преобразования текста T4](../modeling/customizing-t4-text-transformation.md)|
