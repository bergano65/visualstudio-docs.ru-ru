---
title: "Ошибка компилятора CS0825 | Microsoft Docs"
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
  - "CS0825"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0825"
ms.assetid: 49393d23-ec5f-4b44-a3fd-7e0a95ac0edd
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0825
Контекстное ключевое слово var может использоваться только в объявлении локальной переменной.  
  
 Неявное типизирование с ключевым словом `var` может применяться только к переменным в области локального метода.  
  
### Исправление ошибки  
  
1.  Если переменная принадлежит к области класса, задайте ей явный тип.  В противном случае переместите ее в метод, где она будет использоваться.  
  
## Пример  
 В следующем коде возникает ошибка CS0825, поскольку `var` используется в поле класса:  
  
```  
// cs0825.cs class Test { private var myField; //CS0825 static int Main() { var a = 1; // var is OK here return -1; } }  
```  
  
## См. также  
 [Неявно типизированные локальные переменные](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)