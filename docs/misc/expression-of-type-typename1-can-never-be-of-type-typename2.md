---
title: "Выражение типа &quot;&lt;имя_типа1&gt;&quot; никогда не может иметь тип &quot;&lt;имя_типа2&gt;&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31430"
  - "bc31430"
helpviewer_keywords: 
  - "BC31430"
ms.assetid: 1d527033-3f6f-4945-b1d3-5ef59a1e1b53
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Выражение типа &quot;&lt;имя_типа1&gt;&quot; никогда не может иметь тип &quot;&lt;имя_типа2&gt;&quot;
Выражение `TypeOf`...`Is` проверяет переменную, ссылающуюся на объект, на тип данных, который она не может содержать.  
  
 В некоторых случаях компилятор может определить, что проверка `TypeOf`...`Is` может завершиться только ошибкой, например, если отсутствует отношение наследования между двумя классами.  
  
 Эту ошибку может вызывать следующий код.  
  
 `Dim refVar as System.Windows.Forms.Form`  
  
 `If TypeOf refVar Is System.Array`  
  
 `End If`  
  
 Так как <xref:System.Windows.Forms.Form> и <xref:System.Array> являются полностью несвязанными типами, компилятор может определить, что выражение `TypeOf`...`Is` возвращает `False` для любого значения `refVar`.  
  
 **Идентификатор ошибки:** BC31430  
  
### Исправление ошибки  
  
-   Проверяйте переменную на реалистичный тип данных или вообще удалите проверку `TypeOf`...`Is`.  
  
## См. также  
 [Оператор TypeOf](/dotnet/visual-basic/language-reference/operators/typeof-operator)   
 [Практическое руководство. Определение типа, на который указывает объектная переменная](../Topic/How%20to:%20Determine%20What%20Type%20an%20Object%20Variable%20Refers%20To%20\(Visual%20Basic\).md)