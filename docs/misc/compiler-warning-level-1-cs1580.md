---
title: "Предупреждение компилятора (уровень 1) CS1580 | Microsoft Docs"
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
  - "CS1580"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1580"
ms.assetid: ffd1b6d7-6cab-47e3-b7fe-c79cb435cddf
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Предупреждение компилятора (уровень 1) CS1580
Недопустимый тип параметра "номер\_параметра" в атрибуте cref XML\-комментария  
  
 При попытке ссылки на перегруженную форму метода компилятор обнаружил синтаксическую ошибку. Обычно это означает, что было указано имя параметра, а не тип. Неправильная строка будет помещена в созданный XML\-файл.  
  
 В следующем примере возникает ошибка CS1580:  
  
```  
// CS1580.cs // compile with: /W:1 /doc:x.xml using System; /// <seealso cref="Test(i)"/>   // CS1580 // try the following line instead // /// <seealso cref="Test(int)"/> public class MyClass { /// <summary>help text</summary> public static void Main() { } /// <summary>help text</summary> public void Test(int i) { } /// <summary>help text</summary> public void Test(char i) { } }  
```