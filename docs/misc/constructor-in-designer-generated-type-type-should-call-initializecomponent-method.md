---
title: "&quot;&lt;конструктор&gt;&quot; в типе &quot;&lt;тип&gt;&quot;, созданном конструктором, должен вызывать метод InitializeComponent | Microsoft Docs"
ms.custom: ""
ms.date: "10/25/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc40054"
  - "bc40054"
helpviewer_keywords: 
  - "BC40054"
ms.assetid: beac93b0-d427-4df6-9582-fd69c7a53673
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;&lt;конструктор&gt;&quot; в типе &quot;&lt;тип&gt;&quot;, созданном конструктором, должен вызывать метод InitializeComponent
Конструктор в созданном конструктором типе не вызывает метод типа `InitializeComponent`.  
  
 Каждый конструктор в созданном конструктором типе должен вызывать метод типа `InitializeComponent`.  
  
 **Идентификатор ошибки:** BC40054  
  
### Исправление ошибки  
  
-   Добавьте вызов метода `InitializeComponent` в конструкторе.  
  
## См. также  
 <xref:Microsoft.VisualBasic.CompilerServices.DesignerGeneratedAttribute>   
 [НЕ В СБОРКЕ. Использование конструкторов и деструкторов](http://msdn.microsoft.com/ru-ru/548eebe1-86c4-4377-b2f5-447cb8be3d90)