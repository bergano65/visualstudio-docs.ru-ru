---
title: "Не удается выбрать дочерние XML-элементы из типа &quot;тип&quot;. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36809"
  - "bc36809"
helpviewer_keywords: 
  - "BC36809"
ms.assetid: 560a3370-f24d-4ca3-93b1-39aabe13c238
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Не удается выбрать дочерние XML-элементы из типа &quot;тип&quot;.
На дочерний XML\-элемент имеется ссылка в объекте, который не относится к типу <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XDocument> или `IEnumerable(Of XElement)`. Дополнительные сведения см. в разделе [Свойство дочерней оси XML](/dotnet/visual-basic/language-reference/xml-axis/xml-descendant-axis-property).  
  
```vb#  
' Generates an error. Dim var = "sample text"...<childElement>  
```  
  
 **Идентификатор ошибки:** BC36809  
  
### Исправление ошибки  
  
-   Убедитесь, что объект, из которого вы ссылаетесь на дочерний элемент, строго типизируется как <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XDocument> или `IEnumerable(Of XElement)`. Ниже представлен пример:  
  
    ```vb#  
    Dim elem As XElement = <root> <child /> </root> Dim var = elem...<child>  
    ```  
  
## См. также  
 [Свойство дочерней оси XML](/dotnet/visual-basic/language-reference/xml-axis/xml-descendant-axis-property)   
 [Свойства оси XML](/dotnet/visual-basic/language-reference/xml-axis/xml-axis-properties)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)