---
title: Доступ к моделям из текстовых шаблонов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, accessing models
ms.assetid: cf65395a-0ca3-4826-89c7-b1869562685c
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e9eba4a919f159462080688c64ed765d3c1fec86
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68871987"
---
# <a name="accessing-models-from-text-templates"></a>Обращение к моделям из текстовых шаблонов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

С помощью текстовых шаблонов можно создавать файлы отчетов, файлы исходного кода и другие текстовые файлы, основанные на моделях доменного языка. Основные сведения о текстовых шаблонах см. в разделе [Создание кода и текстовые шаблоны T4](../modeling/code-generation-and-t4-text-templates.md). Текстовые шаблоны будут работать в экспериментальном режиме при отладке DSL и также будут работать на компьютере, на котором развернут DSL.

> [!NOTE]
> При создании решения DSL в проекте отладки создаются файлы примеров текстовых шаблонов  **\*. TT** . При изменении имен доменных классов эти шаблоны больше не будут работать. Тем не менее, они включают в себя основные необходимые директивы и содержат примеры, которые можно обновить в соответствии с ЯЗЫКОВым стандартом.

 Для доступа к модели из текстового шаблона:

- Установите свойство inherit директивы template в [моделингтексттрансформатион](/previous-versions/bb893209(v=vs.140)). Это обеспечивает доступ к хранилищу.

- Укажите обработчики директив для DSL, к которому требуется получить доступ. При этом загружаются сборки для DSL, чтобы можно было использовать доменные классы, свойства и связи в коде текстового шаблона. Он также загружает указанный файл модели.

  Файл, аналогичный приведенному в следующем примере, создается в проекте отладки при создании [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] решения из шаблона минимального языка DSL. `.tt`

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

 Обратите внимание на следующие моменты, касающиеся этого шаблона:

- Шаблон может использовать доменные классы, свойства и связи, определенные в определении DSL.

- Шаблон загружает файл модели, указанный в `requires` свойстве.

- Свойство в `this` содержит корневой элемент. После этого код может переходить к другим элементам модели. Имя свойства обычно совпадает с именем класса корневого домена вашего DSL. В этом примере это `this.ExampleModel`.

- Несмотря на то, что язык, на котором пишутся C#фрагменты кода, является, можно создать текст любого типа. Можно также написать код в [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] , добавив свойство `language="VB"` в `template` директиву.

- Чтобы выполнить отладку шаблона, `debug="true"` добавьте `template` директиву. Шаблон будет открыт в другом экземпляре [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] при возникновении исключения. Если вы хотите прервать работу отладчика в определенной точке кода, вставьте оператор`System.Diagnostics.Debugger.Break();`

     Дополнительные сведения см. [в разделе Отладка текстового шаблона T4](../modeling/debugging-a-t4-text-template.md).

## <a name="about-the-dsl-directive-processor"></a>Сведения о процессоре директив DSL
 Шаблон может использовать доменные классы, определенные в определении DSL. Это происходит с помощью директивы, которая обычно появляется рядом с началом шаблона. В предыдущем примере это:

```
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>
```

 Имя директивы ( `MyLanguage`в данном примере) является производным от имени вашего DSL. Он вызывает *обработчик директив* , который создается как часть вашего DSL. Его исходный код можно найти в **дсл\женератедкоде\директивепроцессор.КС**.

 Обработчик директив DSL выполняет две основные задачи:

- Он фактически вставляет директивы Assembly и Import в шаблон, который ссылается на DSL. Это позволяет использовать классы доменов в коде шаблона.

- Он загружает файл, указанный в `requires` параметре, и задает свойство в `this` , которое ссылается на корневой элемент загруженной модели.

## <a name="validating-the-model-before-running-the-template"></a>Проверка модели перед запуском шаблона
 Модель можно проверить перед выполнением шаблона.

```
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1';validation='open|load|save|menu'" #>

```

 Обратите внимание на указанные ниже моменты.

1. Параметры `filename` и`validation` разделяются символом ";", и не должно быть других разделителей или пробелов.

2. Список категорий проверки определяет, какие методы проверки будут выполнены. Несколько категорий должны быть разделены символом "&#124;" и не должно быть других разделителей или пробелов.

   Если ошибка обнаружена, она будет отображаться в окне ошибок, а файл результатов будет содержать сообщение об ошибке.

## <a name="Multiple"></a>Доступ к нескольким моделям из текстового шаблона

> [!NOTE]
> Этот метод позволяет считывать несколько моделей в одном шаблоне, но не поддерживает ссылки ModelBus. Сведения о чтении моделей, связанных ссылками ModelBus, см. [в разделе использование Visual Studio ModelBus в текстовом шаблоне](../modeling/using-visual-studio-modelbus-in-a-text-template.md).

 Если требуется получить доступ к нескольким моделям из одного и того же текстового шаблона, необходимо вызвать созданный обработчик директив один раз для каждой модели. Необходимо указать имя файла каждой модели в `requires` параметре. Необходимо указать имена, которые будут использоваться для корневого класса домена в `provides` параметре. Необходимо указать разные значения для `provides` параметров в каждом вызове директивы. Например, предположим, что у вас есть три файла модели с именами Library. XYZ, School. XYZ и "Рабочий. XYZ". Для доступа к ним из одного и того же текстового шаблона необходимо написать три вызова директивы, которые похожи на следующие.

```
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Library.xyz'" provides="ExampleModel=LibraryModel" #>
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='School.xyz'" provides="ExampleModel=SchoolModel" #>
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Work.xyz'" provides="ExampleModel=WorkModel" #>
```

> [!NOTE]
> Этот пример кода предназначен для языка, основанного на шаблоне минимального языкового решения.

 Для доступа к моделям в текстовом шаблоне теперь можно написать код, аналогичный коду, приведенному в следующем примере.

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

## <a name="loading-models-dynamically"></a>Динамическая загрузка моделей
 Если вы хотите определить во время выполнения, какие модели следует загрузить, можно загрузить файл модели динамически в программном коде вместо использования директивы, зависящей от DSL.

 Однако одной из функций директивы DSL является импорт пространства имен DSL, чтобы код шаблона мог использовать доменные классы, определенные в этом DSL. Так как директива не используется, необходимо добавить  **\<> сборки** и  **\<импортировать** директивы > для всех моделей, которые можно загрузить. Это легко, если различные модели, которые можно загрузить, являются экземплярами одного и того же DSL.

 Для загрузки файла наиболее эффективным методом является использование [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ModelBus. В типичном сценарии текстовый шаблон будет использовать директиву DSL для загрузки первой модели обычным способом. Эта модель будет содержать ссылки ModelBus на другую модель. С помощью ModelBus можно открыть модель, на которую указывает ссылка, и получить доступ к определенному элементу. Дополнительные сведения см. в разделе [с помощью Visual Studio ModelBus в текстовом шаблоне](../modeling/using-visual-studio-modelbus-in-a-text-template.md).

 В менее обычном сценарии может потребоваться открыть файл модели, для которого у вас есть только имя файла и который может отсутствовать в текущем [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] проекте. В этом случае файл можно открыть с помощью метода, описанного в разделе [как: Откройте модель из файла в программном коде](../modeling/how-to-open-a-model-from-file-in-program-code.md).

## <a name="generating-multiple-files-from-a-template"></a>Создание нескольких файлов из шаблона
 Если вы хотите создать несколько файлов, например для создания отдельного файла для каждого элемента в модели, существует несколько возможных подходов. По умолчанию из каждого файла шаблона создается только один файл.

### <a name="splitting-a-long-file"></a>Разделение длинного файла
 В этом методе шаблон используется для создания одного файла, разделенного разделителем. Затем файл разбивается на части. Существует два шаблона: один для создания одного файла, а другой — для его разделения.

 **Луптемплате. T4** создает длинный единственный файл. Обратите внимание, что его расширение файла — ". T4", так как оно не должно обрабатываться непосредственно при нажатии кнопки " **преобразовать все шаблоны**". Этот шаблон принимает параметр, указывающий строку разделителя, разделяющую сегменты.

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

 `LoopSplitter.tt``LoopTemplate.t4`вызывает, а затем разделяет получившийся файл в его сегменты. Обратите внимание, что этот шаблон не обязательно должен быть шаблоном моделирования, так как он не считывает модель.

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
