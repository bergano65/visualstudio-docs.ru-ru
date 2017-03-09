---
title: "XML-литерал можно использовать здесь, только если заключить его в скобки | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31198"
  - "vbc31198"
helpviewer_keywords: 
  - "BC31198"
ms.assetid: 97b16076-39ff-430a-9c65-073d01bcb08e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# XML-литерал можно использовать здесь, только если заключить его в скобки
Объявление XML\-литерала используется в неоднозначном для компилятора месте [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. То есть компилятор [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] не может определить, является ли символ "меньше чем" \(\<\) оператором сравнения или началом XML\-литерала. Примером является следующий код:  
  
 \[Visual Basic\]  
  
```  
' Generates an error. Dim queryResult = From element In elements _ Where <sample>Value</sample> = "Value" _ Select element  
```  
  
 **Идентификатор ошибки:** BC31198  
  
### Исправление ошибки  
  
-   Заключите объявление XML\-литерала в скобки, как показано в следующем примере:  
  
    ```vb#  
    Dim queryResult = From element In elements _ Where (<sample> Value</sample>) = "Value" _ Select element  
    ```  
  
-   Измените код, чтобы он ссылался на существующий XML\-литерал, как показано в следующем примере:  
  
    ```vb#  
    Dim queryResult = From element In elements _ Where e.<sample>.Value = "Value" _ Select element  
    ```  
  
## См. также  
 [XML\-литералы](/dotnet/visual-basic/language-reference/xml-literals/index)   
 [Свойства оси XML](/dotnet/visual-basic/language-reference/xml-axis/xml-axis-properties)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)