---
title: "Ошибка компилятора CS0409 | Microsoft Docs"
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
  - "CS0409"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0409"
ms.assetid: 23d86c13-7978-41b7-a087-ffcea52476fa
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0409
Предложение ограничения для параметра типа "параметр\_типа" уже указано. Все ограничения для параметра типа должны быть указаны в одном предложении where.  
  
 Обнаружено несколько предложений ограничений \(предложений where\) для одного параметра типа. Удалите лишние предложения where или исправьте их так, чтобы в каждом предложении был уникальный параметр типа.  
  
```  
// CS0409.cs interface I { } class C<T1, T2> where T1 : I where T1 : I  // CS0409 – T1 used twice { }  
```