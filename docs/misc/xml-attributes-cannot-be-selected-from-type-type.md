---
title: "Не удается выбрать атрибуты XML из типа &quot;тип&quot; | Microsoft Docs"
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
  - "bc36808"
  - "vbc36808"
helpviewer_keywords: 
  - "BC36808"
ms.assetid: 76b2605c-3d9b-4e56-ba3f-99c60c668290
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Не удается выбрать атрибуты XML из типа &quot;тип&quot;
На атрибут XML имеется ссылка для получения объекта, который не относится к типу <xref:System.Xml.Linq.XElement> или `IEnumerable(Of XElement)`. Для получения дополнительной информации см. [Свойство оси атрибута XML](/dotnet/visual-basic/language-reference/xml-axis/xml-attribute-axis-property).  
  
```vb#  
' Generates an error. Dim var = "sample text".@attr  
```  
  
 **Идентификатор ошибки:** BC36808  
  
### Исправление ошибки  
  
-   Убедитесь в том, что объект, из которого вы ссылаетесь на атрибут, строго типизируется как <xref:System.Xml.Linq.XElement> или `IEnumerable(Of XElement)`. Ниже представлен пример:  
  
    ```vb#  
    Dim elem As XElement = <root attr="value"/> Dim var = elem.@attr  
    ```  
  
## См. также  
 [Свойство оси атрибута XML](/dotnet/visual-basic/language-reference/xml-axis/xml-attribute-axis-property)   
 [Свойства оси XML](/dotnet/visual-basic/language-reference/xml-axis/xml-axis-properties)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)