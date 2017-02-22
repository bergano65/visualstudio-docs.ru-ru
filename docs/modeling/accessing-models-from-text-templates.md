---
title: "Обращение к моделям из текстовых шаблонов | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "текстовые шаблоны, доступ к моделям"
ms.assetid: cf65395a-0ca3-4826-89c7-b1869562685c
caps.latest.revision: 33
caps.handback.revision: 33
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Обращение к моделям из текстовых шаблонов
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

С помощью текстовых шаблонов, можно создать файлы отчетов, файлы исходного кода и другие текстовые файлы, основанные на моделях доменного языка.  Основные сведения о текстовых шаблонах см. в разделе [Code Generation and T4 Text Templates](../modeling/code-generation-and-t4-text-templates.md).  Текстовые шаблоны будут работать в экспериментальном режиме при отладке в DSL, а также будут работать на компьютере, на котором выполняется развертывание DSL.  
  
> [!NOTE]
>  При создании решения DSL, текстовый шаблон образца **\*.tt** файлы создаются в проекте отладки.  При изменении доменных имен классов, эти шаблоны больше не будут работать.  Однако они включают основные рекомендации, которые необходимы, а также приведены примеры, которые можно обновлять, чтобы он соответствовал свой DSL.  
  
 Доступ к модели из текстового шаблона:  
  
-   Задайте свойству наследование директивы шаблона <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation>.  Это обеспечивает доступ к хранилищу.  
  
-   Укажите процессоры директив для DSL, который требуется получить доступ.  Это загружает сборки для DSL, что позволяет использовать его доменных классы, свойства и связи в коде данного текстового шаблона.  Он также загружает файл модели.  
  
 A `.tt` файл, аналогичный следующему примеру создан в проекте отладки при создании новой  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] решение из шаблона язык DSL минимального.  
  
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
  
 Обратите внимание на следующие моменты об этом шаблоне:  
  
-   Шаблон может использовать доменных классы, свойства и связи, определенные в определении DSL.  
  
-   Шаблон загружает файл, указанный в модели `requires` свойство.  
  
-   Свойство in `this` содержит корневой элемент.  Оттуда, код может переходить к другим элементам модели.  Имя свойства обычно такая же, как и класс для корневого домена DSL.  В этом примере он `this.ExampleModel`.  
  
-   Хотя язык, на котором фрагменты кода записываются c\#, можно создать текст любого типа.  Можно также написать код в пределах [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] за счет добавления свойства  `language="VB"` к  `template` директива.  
  
-   Чтобы отладить шаблон, добавление `debug="true"` к  `template` директива.  Шаблон будет открыто в другом экземпляре [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] при возникновении исключения.  Если необходимо переключиться в режим отладчика на конкретный шаг в коде, вставьте выписку `System.Diagnostics.Debugger.Break();`  
  
     Дополнительные сведения см. в разделе [Debugging a T4 Text Template](../modeling/debugging-a-t4-text-template.md).  
  
## О процессора директив DSL  
 Шаблон может использовать доменных классы, указанные в определении DSL.  Это принесено рядом с директивой, обычно отображается в начале шаблона.  В предыдущем примере, следующие.  
  
```  
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>  
```  
  
 Имя директивы \( `MyLanguage`в этом примере\) является производным от имени имеющегося DSL.  Он вызывает a *процессор директив* будет создано как часть DSL.  Можно найти его в исходный код **Dsl\\GeneratedCode\\DirectiveProcessor.cs**.  
  
 Процессор директив DSL выполняет 2 основных задач.  
  
-   Он фактически вставляет директивы сборки и импорта в шаблон, который ссылается на свой DSL.  Это позволяет использовать классы доменных в коде шаблона.  
  
-   Он загружает файл, указанный в `requires` параметр, а для свойства in  `this` это относится к корневому элементу, загружаемой модели.  
  
## Проверка модели перед выполнением шаблон  
 Можно заставить модели необходимо проверить перед шаблон выполняется.  
  
```  
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1';validation='open|load|save|menu'" #>  
  
```  
  
 Обратите внимание, что:  
  
1.  `filename` и  `validation` параметры разделяются знаком "; должно быть" и другие разделители или пробелы.  
  
2.  Список категорий проверки определяет, какие методы проверки выполняются.  Несколько категорий должны быть разделены с "&#124;должно быть" и другие разделители или пробелы.  
  
 Если обнаружена ошибка, то будет отмечено в окне ошибок и файл результата будет содержать сообщение об ошибке.  
  
##  <a name="Multiple"></a> Доступ к несколько моделей из текстового шаблона  
  
> [!NOTE]
>  Этот метод позволяет считывать нескольких моделей в том же шаблоне, но не поддерживает ссылки ModelBus.  Для считывания модели, interlinked ссылка ModelBus см. в разделе [Использование Visual Studio ModelBus в текстовом шаблоне](../modeling/using-visual-studio-modelbus-in-a-text-template.md).  
  
 Если необходимо получить доступ к более одной модели на основе одного и того же текстового шаблона, необходимо вызвать, созданный процессор директив один раз для каждой модели.  Необходимо указать имя файла в каждой модели `requires` параметр.  Необходимо указать имена, которые необходимо использовать для класса корневого домена `provides` параметр.  Необходимо указать различные значения `provides` параметры в каждом из директивных вызовов.  Например, предположим, что имеется 3 Library.xyz с именем файла модели, School.xyz и Work.xyz.  Для обращения к ним из одного и того же текстового шаблона, необходимо написать 3 директивных вызова, который будет аналогична разметке, которая приведена ниже один.  
  
```  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Library.xyz'" provides="ExampleModel=LibraryModel" #>  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='School.xyz'" provides="ExampleModel=SchoolModel" #>  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Work.xyz'" provides="ExampleModel=WorkModel" #>  
```  
  
> [!NOTE]
>  Этот пример кода для языка, который основан на шаблоне решения подобие уровень минимального языка.  
  
 Чтобы получить доступ к модели в текстовом шаблоне, теперь можно написать код, аналогичный код в следующем примере.  
  
```c#  
<#  
foreach (ExampleElement element in this.LibraryModel.Elements)  
...  
foreach (ExampleElement element in this.SchoolModel.Elements)  
...  
foreach (ExampleElement element in this.WorkModel.Elements)  
...  
#>  
```  
  
```vb#  
<#  
For Each element As ExampleElement In Me.LibraryModel.Elements  
...  
For Each element As ExampleElement In Me.SchoolModel.Elements  
...  
For Each element As ExampleElement In Me.WorkModel.Elements  
...  
#>  
```  
  
## Модель динамической загрузки  
 Если необходимо указать во время выполнения, которая моделирует для загрузки, можно загружать динамически файл модели в программном коде, вместо директивы DSL\-специфического.  
  
 Однако одной из функций рекомендации DSL\-специфического импортировать пространство имен DSL, поэтому код шаблона мог использовать указанные доменных классы в этом DSL.  Так как не использовать директиву, необходимо добавить **\<assembly\>** и  **\<import\>** рекомендации для всех моделей, которые могут загрузить.  Это легко если различные модели, можно загружать все экземпляры одного и того же DSL.  
  
 Чтобы загрузить файл, наиболее эффективный метод с помощью [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus.  В типичном сценарии, пользовательский текстовый шаблон будет использовать директиву DSL\-специфического для загрузки первую модель обычным способом.  Модель содержит ссылки ModelBus на другой модели.  Можно использовать ModelBus, чтобы открыть связанную модель и доступа к указанный элемент.  Дополнительные сведения см. в разделе [Использование Visual Studio ModelBus в текстовом шаблоне](../modeling/using-visual-studio-modelbus-in-a-text-template.md).  
  
 В менее обычном сценарии, может понадобиться открыть файл модели, для которого имеется только имя файла и который не может находиться в любом месте [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] этот проект.  В этом случае файл можно открыть с помощью метода, описанного в пределах [Практическое руководство. Открытие модели из файла в коде программы](../modeling/how-to-open-a-model-from-file-in-program-code.md).  
  
## Создание нескольких файлов из шаблона  
 Если требуется создать несколько файлов \- например, создать отдельный файл для каждого элемента модели, несколько возможных подходов.  По умолчанию только один файл, созданный из каждого файла шаблона.  
  
### Разбейте файл long  
 В этом методе используется шаблон для создания одного файла, разделенных разделителями.  Затем следует разделить файл в его части.  2 Одного шаблона, чтобы создать один файл, а другой для разделения его.  
  
 **LoopTemplate.t4** создает long отдельный файл.  Обратите внимание, что его расширение файла ".t4", так как они не должны обрабатываться непосредственно при щелчке **Преобразовать все шаблоны**.  Этот шаблон принимает параметр, который определяет строку разделителя, разделяющая сегменты:  
  
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
  
 `LoopSplitter.tt` вызывает  `LoopTemplate.t4`, а затем разделяет результирующий файл в его сегменты.  Обратите внимание, что этот шаблон не может быть шаблоном моделирования, поскольку он не выполняет чтение модели.  
  
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