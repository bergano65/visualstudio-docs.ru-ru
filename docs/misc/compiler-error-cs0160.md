---
title: "Ошибка компилятора CS0160 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0160"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0160"
ms.assetid: 4ef07061-8ef5-42d9-b043-3f81307d569f
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0160
Предыдущее предложение catch уже перехватывает все исключения этого типа или супертипа \("тип"\).  
  
 Ряд операторов **catch** должен быть указан в порядке убывания поколения наследования. Например, наиболее производные объекты должны быть первыми.  
  
 Дополнительные сведения см. в разделах [Операторы обработки исключений](/dotnet/csharp/language-reference/keywords/exception-handling-statements) и [Исключения и обработка исключений](/dotnet/csharp/programming-guide/exceptions/exceptions-and-exception-handling).  
  
 В следующем примере возникает ошибка CS0160:  
  
```  
// CS0160.cs public class MyClass2 : System.Exception {} public class MyClass { public static void Main() { try {} catch(System.Exception) {}   // Second-most derived; should be second catch catch(MyClass2) {}   // CS0160  Most derived; should be first catch } }  
```