---
title: "Ошибка компилятора CS0268 | Microsoft Docs"
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
  - "CS0268"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0268"
ms.assetid: a4faca71-8b4a-4f22-a89e-59d92ced48cb
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0268
Недопустимый импортированный тип "тип". Он содержит циклическую зависимость базового класса.  
  
 Эта ошибка возникает, если тип, импортированный из другого языка, содержит циклическую зависимость базового класса. Такие типы нельзя использовать в программах C\#. Чтобы устранить эту ошибку, проверьте типы, импортированные из других языков, во всех связанных сборках или модулях.