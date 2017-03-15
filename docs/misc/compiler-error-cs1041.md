---
title: "Ошибка компилятора CS1041 | Microsoft Docs"
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
  - "CS1041"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1041"
ms.assetid: 9f62c058-cd28-4cb5-835c-d0f25f4fd08e
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1041
Требуется идентификатор, "ключевое слово" является ключевым словом  
  
 Вместо ожидавшегося идентификатора обнаружено зарезервированное слово языка C\#. Замените [ключевое слово](/dotnet/csharp/language-reference/keywords/index) пользовательским идентификатором.  
  
## Пример  
 Следующий пример приводит к возникновению ошибки CS1041:  
  
```  
// CS1041a.cs class MyClass { public void f(int long)   // CS1041 // Try the following instead: // public void f(int i) { } public static void Main() { } }  
```  
  
## Пример  
 При импорте кода из другого языка программирования, в котором используется другой набор зарезервированных слов, можно изменить зарезервированный идентификатор с помощью префикса @, как показано в приведенном ниже примере.  
  
 Идентификатор с префиксом `@` называется буквальным идентификатором.  
  
```  
// CS1041b.cs class MyClass { public void f(int long)   // CS1041 // Try the following instead: // public void f(int @long) { } public static void Main() { } }  
```