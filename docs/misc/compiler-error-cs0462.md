---
title: "Ошибка компилятора CS0462 | Microsoft Docs"
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
  - "CS0462"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0462"
ms.assetid: 0732b12d-0f7a-47d5-bc54-8b6147d7249f
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0462
Наследуемые члены "член1" и "член2" имеют одинаковую сигнатуру в типе "тип", поэтому их нельзя переопределить  
  
 Эта ошибка возникает при введении универсальных типов. Как правило, наличие в классе двух версий одного метода с одинаковыми сигнатурами невозможно. Но в случае универсальных типов можно определить универсальный метод, который дублирует другой метод в случае создания экземпляра с определенным типом.  
  
## Пример  
 При создании экземпляра типа `C<int>` создаются две версии метода `F` с одинаковыми сигнатурами, поэтому при выполнении переопределения в классе `D` компилятор не может решить, какой из них нужно переопределять.  
  
 Следующий пример приводит к возникновению ошибки CS0462:  
  
```  
// CS0462.cs // compile with: /target:library class C<T> { public virtual void F(T t) {} public virtual void F(int t) {} } class D : C<int> { public override void F(int t) {}   // CS0462 }  
```