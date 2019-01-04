---
title: Обращение к моделям из текстовых шаблонов
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, accessing models
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 364e39744f403e83847d983e02843bf538bf5c57
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53856869"
---
# <a name="accessing-models-from-text-templates"></a>Обращение к моделям из текстовых шаблонов
С помощью текстовых шаблонов, можно создать файлы отчетов, файлы исходного кода и другие текстовые файлы, которые основаны на модели доменного языка. Основные сведения о текстовых шаблонах см. в разделе [создание кода и текстовые шаблоны T4](../modeling/code-generation-and-t4-text-templates.md). Текстовые шаблоны будут работать в экспериментальном режиме, при отладке DSL и также будет работать на компьютере, на котором вы развернули DSL.

> [!NOTE]
>  При создании решения DSL, пример текстового шаблона  **\*.tt** файлы создаются в отладки проекта. Когда вы изменяете имена классов доменов, эти шаблоны больше не будет работать. Тем не менее они включают основные директивы, которые необходимы и приведены примеры, которые можно обновить в соответствии с DSL.

 Доступ к модели из текстового шаблона:

- Задайте для свойства наследования в директиве template <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation>. Это обеспечивает доступ к Store.

- Укажите процессоры директив для DSL, который необходимо получить доступ. Это загружает сборки для DSL, которые можно использовать его доменные классы, свойства и отношения в коде текстового шаблона. Кроме того, он загружает вами файл модели.

  Объект `.tt` файл, как в следующем примере создается в проект "Отладка", при создании нового решения Visual Studio на основе шаблона минимальный язык DSL.

```
<#@ template inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>
<#@ output extension=".txt" #>
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>

This text will be output directly.

This is the name of the model: <#= this.ModelRoot.Name #>

Here is a list of elements in the model:
<#
  // When you change the DSL Definition, some of the code below may not work.
  foreach (ExampleElement element in this.ExampleModel.Elements)
  {#>
<#= element.Name #>
<#
  }
#>
```

 Обратите внимание на следующие аспекты этого шаблона:

- Шаблон можно использовать классы доменов, свойства и отношения, заданные в определении DSL.

- Шаблон загружает файл модели, указываемое в `requires` свойство.

- Свойства в `this` содержит корневой элемент. После этого кода можно перейти к другим элементам модели. Имя свойства обычно является таким же, как корневой класс домена DSL. В этом примере это `this.ExampleModel`.

- Несмотря на то, что является языком, в котором записываются фрагменты кода C#, вы можете создать текстом любого типа. Кроме того, можно написать код [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] , добавив свойство `language="VB"` для `template` директива.

- Чтобы отладить шаблон, добавьте `debug="true"` для `template` директива. Шаблон будет открыт в другом экземпляре Visual Studio при возникновении исключения. Если вы хотите переключиться в режим отладчика в определенный момент в коде, инструкция insert `System.Diagnostics.Debugger.Break();`

   Дополнительные сведения см. в разделе [отладка текстового шаблона T4](../modeling/debugging-a-t4-text-template.md).

## <a name="about-the-dsl-directive-processor"></a>О процессор директив DSL
 Шаблон может использовать доменных классов, которые определены в определении DSL. Переводится директиве, которая обычно появляется в начале шаблона. В предыдущем примере может принимать следующие значения.

```
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>
```

 Имя директивы ( `MyLanguage`, в этом примере) является производным от имени вашего DSL. Он вызывает *процессора директив* , созданный как часть вашего DSL. Вы найдете его исходный код в **Dsl\GeneratedCode\DirectiveProcessor.cs**.

 Процессор директив DSL выполняет две основные задачи:

-   Он вставляет директивы сборки и импорта в шаблон, который ссылается на DSL. Это позволяет использовать классы доменов в коде шаблона.

-   Он загружает файл, указанный в `requires` параметра и задает свойство в `this` , указывающий на корневой элемент загружаемой модели.

## <a name="validating-the-model-before-running-the-template"></a>Проверка модели перед запуском шаблона
 Может привести к модели быть проверены до выполнения шаблона.

```
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1';validation='open|load|save|menu'" #>
```

 Обратите внимание на указанные ниже моменты.

1. `filename` И `validation` параметров разделены символом «;» и должен существовать другие разделители или пробелы.

2. Список категорий проверки определяет, какие методы проверки будут выполняться. Несколько категорий, которые должны быть разделены с помощью "&#124;" и должен существовать другие разделители или пробелы.

   Если обнаруживается ошибка, оно будет отмечено в окне ошибок и файл результатов будет содержать сообщение об ошибке.

## <a name="Multiple"></a> Доступ к несколько моделей из текстового шаблона

> [!NOTE]
>  Этот метод позволяет считывать несколько моделей, в том же шаблоне, но не поддерживает ссылки ModelBus. См. в статье моделей, которые взаимосвязаны с ссылки ModelBus [с помощью Visual Studio ModelBus в текстовом шаблоне](../modeling/using-visual-studio-modelbus-in-a-text-template.md).

 Если вы хотите получить доступ к более чем одной модели из одного текстового шаблона, необходимо вызвать генерируемым обработчиком директив один раз для каждой модели. Необходимо указать имя файла для каждой модели в `requires` параметра. Необходимо указать имена, которые вы хотите использовать для корневого доменного класса в `provides` параметра. Необходимо указать разные значения для `provides` параметров в каждом вызовы директив. Например предположим, что у вас есть три файла модели, называется Library.xyz School.xyz и Work.xyz. Для доступа к ним из одного текстового шаблона, необходимо написать три вызова директивы, похожие на приведенные ниже запросы.

```
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Library.xyz'" provides="ExampleModel=LibraryModel" #>
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='School.xyz'" provides="ExampleModel=SchoolModel" #>
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Work.xyz'" provides="ExampleModel=WorkModel" #>
```

> [!NOTE]
>  Этот пример кода предназначен для языка, на основе шаблона решения минимальный язык.

 Для доступа к модели в текстовый шаблон, теперь можно написать код, аналогичный код в следующем примере.

```csharp
<#
foreach (ExampleElement element in this.LibraryModel.Elements)
...
foreach (ExampleElement element in this.SchoolModel.Elements)
...
foreach (ExampleElement element in this.WorkModel.Elements)
...
#>
```

```vb
<#
For Each element As ExampleElement In Me.LibraryModel.Elements
...
For Each element As ExampleElement In Me.SchoolModel.Elements
...
For Each element As ExampleElement In Me.WorkModel.Elements
...
#>
```

## <a name="loading-models-dynamically"></a>Динамическая загрузка модели
 Если вы хотите определить во время выполнения, какие модели для загрузки, можно загрузить файл модели динамически в коде программы, вместо того чтобы использовать директиву определенного DSL.

 Тем не менее одной из функций DSL конкретных директивы является импорт пространства имен доменного языка, таким образом, чтобы код шаблона можно использовать доменных классов, определенных в этом DSL. Поскольку директива не используется, необходимо добавить  **\<сборки >** и  **\<импорта >** директивы для всех моделей, которые могут загружать. Это просто, если различные модели, которые могут загружать являются экземплярами класса же DSL.

 Загрузить файл, самый эффективный способ — с помощью Visual Studio ModelBus. В типичном сценарии текстовый шаблон будет использовать директиву определенного DSL для загрузки в первой модели обычным способом. Эта модель будет содержать ссылки ModelBus к другой модели. ModelBus можно использовать для открытия соответствующей моделью и получить доступ к конкретному элементу. Дополнительные сведения см. в разделе [с помощью Visual Studio ModelBus в текстовом шаблоне](../modeling/using-visual-studio-modelbus-in-a-text-template.md).

 В менее обычные сценарии может потребоваться открыть файл модели, для которого у вас есть только имя файла, который может оказаться в текущем проекте Visual Studio. В этом случае можно открыть файл с помощью метода, описанного в [как: Открытие модели из файла в коде программы](../modeling/how-to-open-a-model-from-file-in-program-code.md).

## <a name="generating-multiple-files-from-a-template"></a>Создание нескольких файлов из шаблона
 Если вы хотите создавать несколько файлов - к примеру, создать отдельный файл для каждого элемента в модели, существует несколько возможных подходов. По умолчанию будет создан только один файл из каждого файла шаблона.

### <a name="splitting-a-long-file"></a>Разбиение длинных файла
 В этом методе использовать шаблон для создания одного файла, разделены разделителем. Затем файл разделить на части. Имеется два шаблона, один для создания одного, а другой для разделения.

 **LoopTemplate.t4** создает много один файл. Обратите внимание, что расширение файла «.t4», так как он не будут обрабатываться непосредственно при нажатии кнопки **преобразовать все шаблоны**. Этот шаблон принимает параметр, указывающий строку разделителя, разделяющий сегменты:

```
<#@ template ninherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>
<#@ parameter name="delimiter" type="System.String" #>
<#@ output extension=".txt" #>
<#@ MyDSL processor="MyDSLDirectiveProcessor" requires="fileName='SampleModel.mydsl1';validation='open|load|save|menu'" #>
<#
  // Create a file segment for each element:
  foreach (ExampleElement element in this.ExampleModel.Elements)
  {
    // First item is the delimiter:
#>
<#= string.Format(delimiter, element.Id) #>

   Element: <#= element.Name #>
<#
   // Here you generate more content derived from the element.
  }
#>
```

 `LoopSplitter.tt` вызывает `LoopTemplate.t4`, а затем полученный файл на сегменты. Обратите внимание на то, что этот шаблон не быть шаблон моделирования, так как он не поддерживает модели.

```
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ import namespace="Microsoft.VisualStudio.TextTemplating" #>
<#@ import namespace="System.Runtime.Remoting.Messaging" #>
<#@ import namespace="System.IO" #>

<#
  // Get the local path:
  string itemTemplatePath = this.Host.ResolvePath("LoopTemplate.t4");
  string dir = Path.GetDirectoryName(itemTemplatePath);

  // Get the template for generating each file:
  string loopTemplate = File.ReadAllText(itemTemplatePath);

  Engine engine = new Engine();

  // Pass parameter to new template:
  string delimiterGuid = Guid.NewGuid().ToString();
  string delimiter = "::::" + delimiterGuid + ":::";
  CallContext.LogicalSetData("delimiter", delimiter + "{0}:::");
  string joinedFiles = engine.ProcessTemplate(loopTemplate, this.Host);

  string [] separateFiles = joinedFiles.Split(new string [] {delimiter}, StringSplitOptions.None);

  foreach (string nameAndFile in separateFiles)
  {
     if (string.IsNullOrWhiteSpace(nameAndFile)) continue;
     string[] parts = nameAndFile.Split(new string[]{":::"}, 2, StringSplitOptions.None);
     if (parts.Length < 2) continue;
#>
 Generate: [<#= dir #>] [<#= parts[0] #>]
<#
     // Generate a file from this item:
     File.WriteAllText(Path.Combine(dir, parts[0] + ".txt"), parts[1]);
  }
#>
```