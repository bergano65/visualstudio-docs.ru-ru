---
title: "Ошибка компилятора CS1679 | Microsoft Docs"
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
  - "CS1679"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1679"
ms.assetid: c42e9bca-212a-458e-88f8-b81c812436bb
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1679
Недопустимый внешний псевдоним для "\/reference"; "идентификатор" не является допустимым идентификатором  
  
 При использовании функции внешних псевдонимов сборки параметра **\/reference** текст, следующий за **\/reference:** и перед "\=", должен быть допустимым идентификатором C\# или ключевым словом согласно спецификации языка C\#.  
  
 Чтобы исправить эту ошибку, измените текст перед "\=" на допустимый идентификатор C\# или ключевое слово.  
  
## Пример  
 В следующем примере возникает ошибка CS1679.  
  
```  
// CS1679.cs // compile with: /reference:123$BadIdentifier%=System.dll class TestClass { static void Main() { } }  
```