---
title: "Невозможно выбрать элементы XML из типа &quot;тип&quot; | Microsoft Docs"
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
  - "vbc36807"
  - "bc36807"
helpviewer_keywords: 
  - "BC36807"
ms.assetid: 01c19899-2b44-41e9-a99c-35edfa0deaf1
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Невозможно выбрать элементы XML из типа &quot;тип&quot;
На дочерний элемент XML имеется ссылка для получения объекта, который не относится к типу <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XDocument> или `IEnumerable(Of XElement)`. Для получения дополнительной информации см. [Свойство дочерней оси XML](/dotnet/visual-basic/language-reference/xml-axis/xml-child-axis-property).  
  
```vb#  
' Generates an error. Dim var = "sample text".<child>  
```  
  
 **Идентификатор ошибки:** BC36807  
  
### Исправление ошибки  
  
-   Убедитесь, что объект, из которого вы ссылаетесь на атрибут, строго типизируется как <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XDocument> или `IEnumerable(Of XElement)`. Ниже представлен пример:  
  
    ```vb#  
    Dim elem As XElement = <root> <child /> </root> Dim var = elem.<child>  
    ```  
  
## См. также  
 [Свойство дочерней оси XML](/dotnet/visual-basic/language-reference/xml-axis/xml-child-axis-property)   
 [Свойства оси XML](/dotnet/visual-basic/language-reference/xml-axis/xml-axis-properties)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)