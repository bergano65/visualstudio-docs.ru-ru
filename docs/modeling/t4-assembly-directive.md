---
title: "T4 Assembly Directive | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 44949749-ce3c-4fb5-8690-a17f1564ac2f
caps.latest.revision: 4
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 4
---
# T4 Assembly Directive
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

В текстовом шаблоне времени проектирования [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] директива `assembly` загружает сборку, чтобы в коде шаблона можно было использовать ее типы.  Это дает эффект, аналогичный добавлению ссылки на сборку в проекте [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Общие сведения о создании текстовых шаблонов см. в разделе [Writing a T4 Text Template](../modeling/writing-a-t4-text-template.md).  
  
> [!NOTE]
>  В текстовом шаблоне времени выполнения \(предварительно обработанном\) директива `assembly` не требуется.  Вместо этого требуется добавить нужные сборки в раздел **Ссылки** проекта [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Использование директивы Assembly  
 Синтаксис директивы таков:  
  
```  
<#@ assembly name="[assembly strong name|assembly file name]" #>  
```  
  
 Имя сборки должно быть одним из следующих:  
  
-   Строгое имя сборки в глобальном кэше сборок, такое как `System.Xml.dll`.  Кроме того, можно использовать полную форму, такую как `name="System.Xml, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"`.  Дополнительные сведения см. в разделе <xref:System.Reflection.AssemblyName>.  
  
-   абсолютный путь к сборке;  
  
 Синтаксис `$(variableName)` можно использовать для ссылки на переменные [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], такие как `$(SolutionDir)`, а синтаксис `%VariableName%` — для ссылки на переменные среды.  Примеры.  
  
```  
<#@ assembly name="$(SolutionDir)\MyProject\bin\Debug\SomeLibrary.Dll" #>  
```  
  
 В предварительно преобразованном текстовом шаблоне директива assembly не производит никакого эффекта.  Вместо нее включите необходимые ссылки в раздел **Ссылки** проекта [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Дополнительные сведения см. в разделе [Run\-Time Text Generation with T4 Text Templates](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
## Стандартные сборки  
 Следующие сборки загружаются автоматически, поэтому для них не нужно создавать директивы сборки:  
  
-   `Microsoft.VisualStudio.TextTemplating.1*.dll`  
  
-   `System.dll`  
  
-   `WindowsBase.dll`  
  
 При использовании пользовательской директивы процессор директив может загружать дополнительные сборки.  Например, при создании шаблонов для доменного языка \(DSL\) не требуется создавать директивы сборки для следующих сборок:  
  
-   `Microsoft.VisualStudio.Modeling.Sdk.1*.dll`  
  
-   `Microsoft.VisualStudio.Modeling.Sdk.Diagrams.1*.dsl`  
  
-   `Microsoft.VisualStudio.TextTemplating.Modeling.1*.dll`  
  
-   Сборка, содержащая доменный язык.  
  
##  <a name="msbuild"></a> Использование свойств проекта как в MSBuild, так и в Visual Studio  
 Макросы Visual Studio, такие как $\(SolutionDir\), не работают в MSBuild.  Если требуется преобразовывать шаблоны на компьютере сборки, необходимо использовать свойства проекта.  
  
 Измените CSPROJ\- или VBPROJ\-файл для определения свойства проекта.  В этом примере определяется свойство с именем `myLibFolder`.  
  
```xml  
<!-- Define a project property, myLibFolder: -->  
<PropertyGroup>  
    <myLibFolder>$(MSBuildProjectDirectory)\..\libs</myLibFolder>  
</PropertyGroup>  
  
<!-- Tell the MSBuild T4 task to make the property available: -->  
<ItemGroup>  
    <T4ParameterValues Include="myLibFolder">  
      <Value>$(myLibFolder)</Value>  
    </T4ParameterValues>  
  </ItemGroup>  
  
```  
  
 Теперь можно использовать свойство проекта в текстовых шаблонах, которые будут правильно преобразовываться как в Visual Studio, так и в MSBuild:  
  
```  
<#@ assembly name="$(myLibFolder)\MyLib.dll" #>  
```  
  
## См. также  
 [T4 Include Directive](../modeling/t4-include-directive.md)