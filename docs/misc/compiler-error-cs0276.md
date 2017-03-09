---
title: "Ошибка компилятора CS0276 | Microsoft Docs"
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
  - "CS0276"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0276"
ms.assetid: 0c49017f-c7a9-42a5-9d0a-6f1d82142bd7
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0276
"свойство или индексатор": модификаторы доступности могут использоваться для функций доступа, только если свойство или индексатор содержит обе функции доступа \(get и set\)  
  
 Эта ошибка происходит в том случае, если вы объявляете свойство или индексатор только с одним методом доступа и при этом к этому методу доступа применяется модификатор доступа. Для устранения ошибки удалите модификатор доступа или добавьте второй метод доступа.  
  
## Пример  
 Следующий пример приводит к возникновению ошибок CS0276:  
  
```  
// CS0276.cs public class MyClass { public int Property { protected set { }   // CS0276 } public int Property2 { internal get { }   // CS0276 } }  
```