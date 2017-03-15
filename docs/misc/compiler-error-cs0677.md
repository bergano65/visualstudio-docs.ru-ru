---
title: "Ошибка компилятора CS0677 | Microsoft Docs"
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
  - "CS0677"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0677"
ms.assetid: 6a4a3703-9b44-4c4f-a564-8b437b1cb6b8
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0677
"переменная": поле с модификатором volatile не может иметь тип "тип"  
  
 Поля, объявленные с ключевым словом `volatile`, должны относиться к одному из следующих типов:  
  
-   любой ссылочный тип;  
  
-   любой тип указателя \(в контексте `unsafe`\);  
  
-   типы `sbyte`, **byte**, **short**, `ushort`, `int`, `uint`, `char`, **float**, `bool`;  
  
-   типы перечисления на основе любого из указанных выше типов.  
  
 При компиляции следующего примера возникнет ошибка CS0677:  
  
```  
// CS0677.cs class TestClass { private volatile long i;   // CS0677 public static void Main() { } }  
```