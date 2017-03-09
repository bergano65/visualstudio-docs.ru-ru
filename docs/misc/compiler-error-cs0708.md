---
title: "Ошибка компилятора CS0708 | Microsoft Docs"
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
  - "CS0708"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0708"
ms.assetid: 19e1907f-b78c-4c8b-b78c-eedfd57115f2
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0708
"поле": невозможно объявить члены экземпляров в статическом классе  
  
 Эта ошибка возникает при объявлении не являющегося статическим члена в классе, который объявлен статическим. Невозможно создать экземпляры статических классов, поэтому переменные экземпляра не имеют смысла. Ключевое слово **static** должно применяться ко всем членам статических классов.  
  
 В следующем примере возникает ошибка CS0708:  
  
```  
// CS0708.cs // compile with: /target:library public static class C { int i;  // CS0708 static int j;  // OK }  
```