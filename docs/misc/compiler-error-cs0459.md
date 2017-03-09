---
title: "Ошибка компилятора CS0459 | Microsoft Docs"
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
  - "CS0459"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0459"
ms.assetid: 01b058dd-8d65-4e9d-9de1-d47f9488d22a
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0459
Невозможно получить адрес локальной переменной, доступной только для чтения  
  
 В языке C\# существует три типичных сценария, формирующие локальные переменные только для чтения: `foreach`, `using` и `fixed`. В каждом из этих случаев нельзя выполнять запись в локальную переменную только для чтения или получать ее адрес. Эта ошибка возникает, когда компилятор определяет, что вы пытаетесь получить адрес локальной переменной, доступной только для чтения.  
  
## Пример  
 При компиляции следующего примера возникнет ошибка CS0459 при попытке получить адрес локальной переменной только для чтения в цикле `foreach` и в блоке операторов `fixed`.  
  
```  
// CS0459.cs // compile with: /unsafe class A { public unsafe void M1() { int[] ints = new int[] { 1, 2, 3 }; foreach (int i in ints) { int *j = &i;  // CS0459 } fixed (int *i = &_i) { int **j = &i;  // CS0459 } } private int _i = 0; }  
```