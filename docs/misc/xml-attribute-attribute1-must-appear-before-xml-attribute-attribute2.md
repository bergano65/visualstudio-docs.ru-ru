---
title: "XML-атрибут &quot;атрибут1&quot; должен быть указан до XML-атрибута &quot;атрибут2&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31157"
  - "vbc31157"
helpviewer_keywords: 
  - "BC31157"
ms.assetid: d8d8769e-533d-454e-b145-99955ce45cc5
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# XML-атрибут &quot;атрибут1&quot; должен быть указан до XML-атрибута &quot;атрибут2&quot;
Атрибуты в XML\-литерале документа указаны в неправильном порядке. Правильный порядок атрибутов для XML\-литерала документа строится на основе спецификации XML 1.0. Например, атрибут `encoding` XML\-литерала документа должен следовать непосредственно за атрибутом `version`.  
  
 **Идентификатор ошибки:** BC31157  
  
### Исправление ошибки  
  
-   Измените порядок атрибутов для XML\-литерала документа с помощью правил, указанных в спецификации XML 1.0.  
  
## См. также  
 [XML\-литералы и спецификация XML 1.0](/dotnet/visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification)   
 [XML\-литерал документа](/dotnet/visual-basic/language-reference/xml-literals/xml-document-literal)   
 [XML\-литералы](/dotnet/visual-basic/language-reference/xml-literals/index)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)