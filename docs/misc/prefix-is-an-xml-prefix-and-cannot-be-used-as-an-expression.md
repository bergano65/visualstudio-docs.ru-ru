---
title: "&quot;префикс&quot; является XML-префиксом и не может использоваться в качестве выражения | Microsoft Docs"
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
  - "bc30114"
  - "vbc30114"
helpviewer_keywords: 
  - "BC30114"
ms.assetid: 5cb7c89e-c61b-483a-9369-5285b7cbcf45
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;префикс&quot; является XML-префиксом и не может использоваться в качестве выражения
"префикс" является XML\-префиксом и не может использоваться в качестве выражения. Используйте оператор GetXmlNamespace для создания объекта пространства имен.  
  
 Префикс для пространства имен XML, импортированной с помощью инструкции `Imports`, не может использоваться за пределами XML\-литерала.  
  
 **Идентификатор ошибки:** BC30114  
  
### Исправление ошибки  
  
-   Если необходимо сослаться на часть импортируемого пространства имен XML, используйте оператор `GetXmlNamespace` для получения объекта <xref:System.Xml.Linq.XNamespace>. Используйте этот объект вместо префикса пространства имен XML.  
  
-   Если вы используете префикс пространства имен XML для уточнения XML\-литерала, убедитесь, что для XML\-литерала применяется соответствующий синтаксис.  
  
## См. также  
 [XML\-литералы](/dotnet/visual-basic/language-reference/xml-literals/index)   
 [Оператор Imports \(пространство имен XML\)](/dotnet/visual-basic/language-reference/statements/imports-statement-xml-namespace)   
 [Оператор GetXmlNamespace](/dotnet/visual-basic/language-reference/operators/getxmlnamespace-operator)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)   
 [Знакомство с LINQ в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)