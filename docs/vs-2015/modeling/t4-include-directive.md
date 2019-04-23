---
title: T4 Директива Include | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 8c3de9f3-755a-47c5-a30a-65717dcaaac2
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6b475b8e5c2138c909133aee0440f0dcaea99e13
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60057710"
---
# <a name="t4-include-directive"></a>Директива Include T4
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В текстовый шаблон в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] можно включить текст из другого файла, воспользовавшись директивой `<#@include#>`. Директивы `include` можно разместить в любом месте текстового шаблона перед первым блоком возможностей класса `<#+ ... #>`. Включенные файлы также могут содержать директивы `include` и другие директивы. Это позволяет использовать один и тот же код шаблона и стандартный текст в нескольких шаблонах.  
  
## <a name="using-include-directives"></a>Использование директив Include  
  
```  
<#@ include file="filePath" [once="true"] #>  
```  
  
- Путь `filePath` может быть абсолютным или относительным для текущего файла шаблона.  
  
   Кроме того, отдельные расширения [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] могут задавать собственные каталоги для поиска включенных файлов. Например, при установке пакета Visualization and Modeling SDK (DSL Tools) следующую папку добавляется в список включения: `Program Files\Microsoft Visual Studio 10.0\Common7\IDE\Extensions\Microsoft\DSL SDK\DSL Designer\11.0\TextTemplates`.  
  
   Эти дополнительные папки включения могут зависеть от расширения включающего файла. Например, папка включения DSL Tools доступна только для включающих файлов с расширением `.tt`.  
  
- `filePath` может включать переменные среды, отделенные знаком "%". Пример:  
  
  ```  
  <#@ include file="%HOMEPATH%\MyIncludeFile.t4" #>  
  ```  
  
- В имени включенного файла не обязательно использовать расширение `".tt"`.  
  
   Для включенных файлов можно использовать другое расширение, например `".t4"`. Это обусловлено тем, при добавлении `.tt` файл в проект, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] автоматически задает его **пользовательское средство** свойства `TextTemplatingFileGenerator`. Как правило, не нужно, чтобы включенные файлы преобразовывались по отдельности.  
  
   С другой стороны, нужно помнить, что в некоторых случаях расширение файла влияет на то, в каких дополнительных папках будет выполнен поиск файлов включения. Это может оказаться важным при наличии включенного файла, содержащего другие файлы.  
  
- Включенное содержимое обрабатывается почти так же, как если бы оно было частью включающего текстового шаблона. Однако можно включить файл, содержащий блок возможностей класса `<#+...#>`, даже если за директивой `include` следуют обычный текст и стандартные управляющие блоки.  
  
- Используйте `once="true"`, чтобы убедиться, что шаблон включен только один раз, даже если он вызывался из нескольких других файлов include.  
  
   Этот компонент позволяет легко создавать библиотеку повторно используемых фрагментов T4, который можно включить в будет происходить не беспокоясь, другие фрагмент кода уже включила их.  Например предположим, что имеется библиотека слишком детализирован фрагментов, которые имеют дело с обработкой шаблона и создания C#.  В свою очередь они используются некоторые служебные программы более конкретных задач, таких как создание исключений, которые затем можно использовать с любым шаблоном более специфичные для конкретного приложения. Если нарисовать граф зависимостей, можно увидеть, что некоторые фрагменты кода были бы включены несколько раз. Но параметр `once` предотвращает последующие включения.  
  
  **MyTextTemplate.tt:**  
  
```  
<#@ output extension=".txt" #>  
Output message 1 (from top template).  
<#@ include file="TextFile1.t4"#>  
Output message 5 (from top template).  
<#  
   GenerateMessage(6); // defined in TextFile1.t4  
   AnotherGenerateMessage(7); // defined in TextFile2.t4  
#>  
  
```  
  
 **TextFile1.t4:**  
  
```  
   Output Message 2 (from included file).  
<#@include file="TextFile2.t4" #>  
   Output Message 4 (from included file).  
<#+ // Start of class feature control block.  
void GenerateMessage(int n)  
{  
#>  
   Output Message <#= n #> (from GenerateMessage method).  
<#+  
}  
#>  
  
```  
  
 **TextFile2.t4:**  
  
```  
        Output Message 3 (from included file 2).  
<#+ // Start of class feature control block.  
void AnotherGenerateMessage(int n)  
{  
#>  
       Output Message <#= n #> (from AnotherGenerateMessage method).  
<#+  
}  
#>  
  
```  
  
 **Сгенерированный в результате файл, MyTextTemplate.txt:**  
  
```  
Output message 1 (from top template).  
   Output Message 2 (from included file).  
        Output Message 3 (from included file 2).  
  
   Output Message 4 (from included file).  
  
Output message 5 (from top template).  
   Output Message 6 (from GenerateMessage method).  
       Output Message 7 (from AnotherGenerateMessage method).  
  
```  
  
## <a name="msbuild"></a> Использование свойств проекта в MSBuild и Visual Studio  
 Хотя в директиве include можно использовать макросы Visual Studio, такие как $(SolutionDir), они не работают в MSBuild. Если требуется преобразовывать шаблоны на компьютере сборки, необходимо использовать свойства проекта.  
  
 Измените CSPROJ- или VBPROJ-файл для определения свойства проекта. В этом примере определяется свойство с именем `myIncludeFolder`.  
  
```xml  
<!-- Define a project property, myIncludeFolder: -->  
<PropertyGroup>  
    <myIncludeFolder>$(MSBuildProjectDirectory)\..\libs</myIncludeFolder>  
</PropertyGroup>  
  
<!-- Tell the MSBuild T4 task to make the property available: -->  
<ItemGroup>  
    <T4ParameterValues Include="myIncludeFolder">  
      <Value>$(myIncludeFolder)</Value>  
    </T4ParameterValues>  
  </ItemGroup>  
  
```  
  
 Теперь можно использовать свойство проекта в текстовых шаблонах, которые будут правильно преобразовываться как в Visual Studio, так и в MSBuild:  
  
```  
<#@ include file="$(myIncludeFolder)\defs.tt" #>  
```
