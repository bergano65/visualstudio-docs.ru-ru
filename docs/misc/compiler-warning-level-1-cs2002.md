---
title: "Предупреждение компилятора (уровень 1) CS2002 | Microsoft Docs"
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
  - "CS2002"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2002"
ms.assetid: 4acd054e-d3fe-4be6-a660-53a0a5e8c6a4
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Предупреждение компилятора (уровень 1) CS2002
Исходный файл "файл" указан несколько раз  
  
 Имя файла исходного кода было передано в компилятор несколько раз. Для создания выходного файла вы можете указать файл только один раз.  
  
 Это предупреждение не может быть отменено с помощью параметра [\/nowarn](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option).  
  
 В следующем примере возникает ошибка CS2002:  
  
```  
// CS2002.cs // compile with: CS2002.cs public class A { public static void Main(){} }  
```  
  
 Для создания этой ошибки скомпилируйте пример с помощью командной строки:  
  
```  
csc CS2002.cs CS2002.cs  
```