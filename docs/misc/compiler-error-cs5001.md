---
title: "Ошибка компилятора CS5001 | Microsoft Docs"
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
  - "CS5001"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS5001"
ms.assetid: e1e26e75-84e0-47c7-be8a-3c4fd0d6f497
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS5001
Программа "программа" не содержит статического метода Main, подходящего для точки входа  
  
 Эта ошибка происходит, если в коде, который создает исполняемый файл, отсутствует статический метод [Main](/dotnet/csharp/programming-guide/main-and-command-args/main-and-command-line-arguments) с правильной сигнатурой. Кроме того, эта ошибка происходит, если функция точки входа \(`Main`\) определена с использованием неправильного регистра, например со строчной буквы: `main`.  
  
-   Метод `Main` должен быть объявлен как статический, должен возвращать значение типа [void](/dotnet/csharp/language-reference/keywords/void) или [int](/dotnet/csharp/language-reference/keywords/int) и должен либо не иметь параметров, либо иметь один параметр типа `string[]`.  
  
## Пример  
 Следующий пример приводит к возникновению ошибки CS5001:  
  
```  
// CS5001.cs // CS5001 expected public class a { // Uncomment the following line to resolve. // static void Main() {} }  
```  
  
## См. также  
 [Main\(\) и аргументы командной строки](/dotnet/csharp/programming-guide/main-and-command-args/main-and-command-line-arguments)