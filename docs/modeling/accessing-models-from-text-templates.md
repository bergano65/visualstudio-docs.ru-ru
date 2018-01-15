---
title: "Обращение к моделям из текстовых шаблонов | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: text templates, accessing models
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b1d338c62a6241a0ae77d22c7712ee7449aa5973
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/13/2018
---
# <a name="accessing-models-from-text-templates"></a>Обращение к моделям из текстовых шаблонов
С помощью текстовых шаблонов, можно создавать файлы отчетов, файлы исходного кода и другие текстовые файлы, основанные на моделях доменного языка. Основные сведения о текстовых шаблонах см. в разделе [создание кода и текстовые шаблоны T4](../modeling/code-generation-and-t4-text-templates.md). Текстовые шаблоны будут работать в экспериментальном режиме при отладке DSL и также будет работать на компьютере, на котором вы развернули DSL.  
  
> [!NOTE]
>  При создании решения DSL, пример текстового шаблона  **\*.tt** файлы создаются в отладки проекта. При изменении имена классов домена эти шаблоны больше не будет работать. Тем не менее они основные директивы, которые необходимо включить и приводятся примеры, которые могут быть обновлены в соответствии доменного языка.  
  
 Доступ к модели из текстового шаблона:  
  
-   Задать свойство наследования директивы шаблона <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation>. Это обеспечивает доступ к хранилищу.  
  
-   Укажите процессоров директив для доменный язык, необходимо получить доступ. Это загружает сборки для доменного языка, чтобы могли использовать его доменные классы, свойства и отношения в коде текстового шаблона. Он также загружает файл модели, в котором можно указать.  
  
 Объект `.tt` примерно в следующем примере файл создается в отладка проекта при создании нового [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] решения на основе шаблона минимальной языка DSL.  
  
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
  
-   Шаблон можно использовать доменные классы, свойства и отношения, заданные в определении DSL.  
  
-   Шаблон загружает файл модели, указываемое в `requires` свойство.  
  
-   Свойства в `this` содержит корневой элемент. После этого к другим элементам модели может перемещаться код. Имя свойства обычно совпадает домена в корневом классе доменного языка. В этом примере это `this.ExampleModel`.  
  
-   Хотя язык, на котором написаны фрагментов кода C#, вы можете создать текстом любого типа. Кроме того, можно написать код [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] путем добавления свойства `language="VB"` для `template` директивы.  
  
-   Чтобы отладить шаблон, добавьте `debug="true"` для `template` директивы. Шаблон откроется в другом экземпляре [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] при возникновении исключения. Если вы хотите перейти в отладчик в определенный момент в коде, инструкция insert`System.Diagnostics.Debugger.Break();`  
  
     Дополнительные сведения см. в разделе [отладка текстового шаблона T4](../modeling/debugging-a-t4-text-template.md).  
  
## <a name="about-the-dsl-directive-processor"></a>О процессора директив DSL  
 Шаблон можно использовать доменные классы, которые определены в определении DSL. Переводится директивой, которая обычно появляется в начале шаблона. В предыдущем примере может принимать следующие значения.  
  
```  
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>  
```  
  
 Имя директивы ( `MyLanguage`, в этом примере) является производным от имени для доменного языка. Он вызывает *процессора директив* , создаваемый в составе доменного языка. Можно найти его исходный код в **Dsl\GeneratedCode\DirectiveProcessor.cs**.  
  
 Процессор директив DSL выполняет две основные задачи:  
  
-   Он вставляет директив сборки и импорта в шаблон, который ссылается на доменного языка. Это позволяет использовать в коде шаблона классов домена.  
  
-   Он загружает файл, указанный в `requires` параметра и задает свойство в `this` , ссылается на корневой элемент загружаемой модели.  
  
## <a name="validating-the-model-before-running-the-template"></a>Проверка модели перед запуском шаблона  
 Может привести к модели быть проверены до выполнения шаблона.  
  
```  
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1';validation='open|load|save|menu'" #>  
  
```  
  
 Обратите внимание на указанные ниже моменты.  
  
1.  `filename` И `validation` параметры разделяются с «;», а должно быть другие разделители или пробелы.  
  
2.  Список категорий, проверка определяет, какие методы проверки будут выполнены. Несколько категорий должны разделяться с «&#124;» и должен быть другие разделители или пробелы.  
  
 Если обнаруживается ошибка, оно будет отмечено в окне ошибок и результирующий файл будет содержать сообщение об ошибке.  
  
##  <a name="Multiple"></a>Доступ к несколько моделей из текстового шаблона  
  
> [!NOTE]
>  Этот метод позволяет считывать несколько моделей в шаблоне, но не поддерживает ссылки ModelBus. Модели, которые взаимосвязаны с ModelBus ссылки в разделе [с помощью Visual Studio ModelBus в текстовом шаблоне](../modeling/using-visual-studio-modelbus-in-a-text-template.md).  
  
 Если вы хотите получить доступ к более чем одной моделью из одного текстового шаблона, необходимо вызвать созданный процессора директив один раз для каждой модели. Необходимо указать имя файла, в каждой модели `requires` параметра. Необходимо указать имена, которые вы хотите использовать для класса корневого домена в `provides` параметра. Необходимо указать различные значения для `provides` параметров в каждом вызовы директив. Например предположим, что имеются три модели файлы, называемые Library.xyz, School.xyz и Work.xyz. Для доступа к ним из одного текстового шаблона, необходимо написать три вызова директивы, напоминающие следующие значения.  
  
```  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Library.xyz'" provides="ExampleModel=LibraryModel" #>  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='School.xyz'" provides="ExampleModel=SchoolModel" #>  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Work.xyz'" provides="ExampleModel=WorkModel" #>  
```  
  
> [!NOTE]
>  Этот пример кода является для языка, который основан на шаблоне решения минимальной языка.  
  
 Для доступа к модели в текстовый шаблон, теперь можно написать код, подобный код в следующем примере.  
  
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
 Если вы хотите определить во время выполнения, какие модели для загрузки, можно загрузить файл модели динамически в программном коде, вместо директивы конкретного DSL.  
  
 Одной из функций конкретного DSL директивы то, чтобы импортировать пространство имен DSL, чтобы код шаблона может использовать домен классы, определенные в этом DSL. Поскольку директива не используется, необходимо добавить  **\<сборки >** и  **\<импорта >** директивы для всех моделей, которые может загрузить. Это легко, если различные модели, которые могут загрузить являются экземплярами одного DSL.  
  
 Для загрузки файла, наиболее эффективный способ — использование [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus. В типичном сценарии текстовый шаблон будет использовать директиву конкретного DSL для загрузки в первой модели обычным способом. Эта модель будет содержать ModelBus ссылки на другую модель. ModelBus можно использовать для открытия соответствующей моделью и получить доступ к определенному элементу. Дополнительные сведения см. в разделе [с помощью Visual Studio ModelBus в текстовом шаблоне](../modeling/using-visual-studio-modelbus-in-a-text-template.md).  
  
 В менее обычные сценарии может потребоваться открыть файл модели, для которого у вас есть только имя файла, который может оказаться в текущем [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] проекта. В этом случае можно открыть с помощью метода, описанного в файле [как: открытие модели из файла в программном коде](../modeling/how-to-open-a-model-from-file-in-program-code.md).  
  
## <a name="generating-multiple-files-from-a-template"></a>Создание нескольких файлов из шаблона  
 Если требуется создать несколько файлов - например, для создания отдельного файла для каждого элемента в модели существуют нескольких возможных подходов. По умолчанию только один файл создается из каждого файла шаблона.  
  
### <a name="splitting-a-long-file"></a>Разделение длинный файл  
 В этом методе используется шаблон для создания одного файла, разделены разделителем. Затем файл разделить на части. Существует два шаблона: один для создания одним файлом, а другой для разделения.  
  
 **LoopTemplate.t4** приводит к возникновению ошибки long один файл. Обратите внимание, что его расширение «.t4», так как он не должны обрабатываться непосредственно при нажатии кнопки **преобразовать все шаблоны**. Этот шаблон принимает параметр, который задает строку разделителя, который служит для разделения сегментов:  
  
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
  
 `LoopSplitter.tt`вызывает `LoopTemplate.t4`, а затем разделяет результирующий файл на сегменты. Обратите внимание, что этот шаблон не обязательно должна быть шаблона моделирования, так как он не поддерживает модель.  
  
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