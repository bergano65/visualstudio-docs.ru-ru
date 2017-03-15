---
title: "T4 Import Directive | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 713ca975-b9aa-4210-bf6d-b7660f5b193b
caps.latest.revision: 3
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 3
---
# T4 Import Directive
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

В блоках кода текстового шаблона T4 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] директива `import` позволяет ссылаться на элементы в другом пространстве имен без предоставления полного имени.  Она эквивалентна директиве `using` в C\# или `imports` в [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)].  
  
 Общие сведения о создании текстовых шаблонов T4 см. в разделе [Writing a T4 Text Template](../modeling/writing-a-t4-text-template.md).  
  
## Использование директивы Import  
  
```  
<#@ import namespace="namespace" #>  
```  
  
 В этом примере в коде шаблона можно пропустить явное пространство имен для членов группы System.IO:  
  
```  
<#@ import namespace="System.IO" #>  
<#   
   string fileContent = File.ReadAllText("C:\x.txt"); // System.IO.File  
#>   
The file contains: <#=  fileContent #>  
```  
  
## Стандартные импорты  
 Следующее пространство имен импортируется автоматически, поэтому для него не нужно создавать директиву импорта:  
  
-   `System`  
  
 Кроме того, при использовании пользовательской директивы процессор директив может импортировать некоторые пространства имен автоматически.  
  
 Например, при создании шаблонов для доменного языка \(DSL\) не требуется создавать директивы импорта для следующих пространств имен:  
  
-   `Microsoft.VisualStudio.Modeling`  
  
-   Пространство имен доменного языка  
  
## См. также  
 [T4 Assembly Directive](../modeling/t4-assembly-directive.md)