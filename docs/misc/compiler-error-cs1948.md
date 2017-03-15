---
title: "Ошибка компилятора CS1948 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1948"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1948"
ms.assetid: 3dac3abe-0edd-4ee1-8fb1-bc597ea63e1f
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1948
Переменная диапазона "имя" не может иметь имя, совпадающее с именем параметра типа метода  
  
 Одно и то же пространство объявления не может содержать два объявления одного идентификатора.  
  
### Исправление ошибки  
  
1.  Измените имя переменной диапазона или параметра типа.  
  
## Пример  
 Приведенный ниже пример приводит к возникновению ошибки CS1948, так как идентификатор `T` используется для переменной диапазона и для параметра типа в методе `TestMethod`.  
  
```  
// cs1948.cs using System.Linq; class Test { public void TestMethod<T>(T t) { var x = from T in Enumerable.Range(1, 100) // CS1948 select T; } }  
```