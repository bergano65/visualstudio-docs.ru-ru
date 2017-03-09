---
title: "Ошибка компилятора CS0454 | Microsoft Docs"
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
  - "CS0454"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0454"
ms.assetid: 2c83bc5e-53bb-473e-92aa-5122dadd79d1
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0454
Циклическая зависимость ограничений, включающая "Параметр типа 1" и "Параметр типа 2"  
  
 Данная ошибка возникает, когда в некоторой точке один параметр типа ссылается на другой, а второй параметр типа в свою очередь ссылается на первый. Чтобы устранить эту ошибку, разбейте циклическую зависимость, удалив одно из ограничений. Обратите внимание, что циклическая зависимость ограничений может быть непрямой.  
  
## Пример  
 Следующий код вызывает ошибку CS0454.  
  
```  
// CS0554 using System; public class GenericsErrors { public class G4<T> where T : T { } // CS0454 }  
```  
  
## Пример  
 В следующем примере показана циклическая зависимость между двумя ограничениями типа.  
  
```  
public class Gen<T,U> where T : U where U : T  // CS0454 { }  
```