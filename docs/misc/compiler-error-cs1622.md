---
title: "Ошибка компилятора CS1622 | Microsoft Docs"
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
  - "CS1622"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1622"
ms.assetid: 6b53a777-4cd8-423a-84ff-22ff588044d3
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1622
Итератор не может вернуть значение. Используйте оператор yield return для возвращения значения или yield break для завершения итерации.  
  
 Итератор — это специальная функция, возвращающая значение посредством оператора yield, а не оператора return. Дополнительные сведения см. в разделе **Итераторы**.  
  
 Следующий пример приводит к возникновению ошибки CS1622:  
  
```  
// CS1622.cs // compile with: /target:library using System.Collections; class C : IEnumerable { public IEnumerator GetEnumerator() { return (IEnumerator) this;  // CS1622 yield return this;   // OK } }  
```