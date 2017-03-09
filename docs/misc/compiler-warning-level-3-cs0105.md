---
title: "Предупреждение компилятора (уровень 3) CS0105 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0105"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0105"
ms.assetid: 96d1d5d7-79e9-424f-bbde-f87e88b70003
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Предупреждение компилятора (уровень 3) CS0105
Директива using для "пространство\_имен" ранее встречалась в этом пространстве имен  
  
 [Пространство имен](/dotnet/csharp/language-reference/keywords/namespace), которое должно быть объявлено только один раз, было объявлено несколько раз; удалите все повторяющиеся объявления пространства имен.  
  
 При компиляции следующего примера будет выдано предупреждение CS0105:  
  
```  
// CS0105.cs // compile with: /W:3 using System; using System;   // CS0105 public class a { public static void Main() { } }  
```