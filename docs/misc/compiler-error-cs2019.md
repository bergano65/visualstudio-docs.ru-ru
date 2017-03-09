---
title: "Ошибка компилятора CS2019 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS2019"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2019"
ms.assetid: eafd2531-8b3a-499c-9e12-a605a011396f
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS2019
Недопустимый тип результата для \/target: необходимо указать "exe", "winexe", "library" или "module"  
  
 Использовался параметр компилятора [\/target](/dotnet/csharp/language-reference/compiler-options/target-compiler-option), но был передан недопустимый параметр. Чтобы устранить эту ошибку, перекомпилируйте программу, используя форму параметра **\/target**, подходящую для вашего выходного файла.  
  
 В следующем примере возникает ошибка CS2017:  
  
```  
// CS2019.cs // compile with: /target:libra // CS2019 expected class MyClass { }  
```