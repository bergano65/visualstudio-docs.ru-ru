---
title: "Ошибка компилятора CS0748 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0748"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0748"
ms.assetid: da1935af-a5ea-41f4-84ae-58559b750566
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0748
Несогласованное использование лямбда\-параметра; типы параметров должны быть либо все явными, либо все неявными.  
  
 Если лямбда\-выражение имеет несколько входных параметров, не разрешается, чтобы одни параметры использовали явную типизацию, а другие неявную.  
  
### Исправление ошибки  
  
1.  Предоставьте всем входным параметрам неявные типы или всем им предоставьте явные типы.  
  
## Пример  
 В следующем коде возникает ошибка CS0748, поскольку в лямбда\-выражении только параметру `alpha` присваивается явный тип:  
  
```  
// cs0748.cs class CS0748 { delegate double D(int x, int y); D d = (int alpha, beta) => { return beta / alpha; }; // CS0748 }  
```  
  
## См. также  
 [Лямбда\-выражения](/dotnet/csharp/programming-guide/statements-expressions-operators/lambda-expressions)