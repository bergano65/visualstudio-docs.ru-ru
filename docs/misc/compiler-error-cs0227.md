---
title: "Ошибка компилятора CS0227 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0227"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0227"
ms.assetid: b595a1c9-8204-4ff7-a1d0-258b0b1d6ff7
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0227
Небезопасный код может использоваться только при компиляции с параметром \/unsafe.  
  
 Если исходный код содержит ключевое слово [unsafe](/dotnet/csharp/language-reference/keywords/unsafe), то необходимо также использовать параметр компилятора [\/unsafe](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option). Для получения дополнительной информации см. [Небезопасный код и указатели](/dotnet/csharp/programming-guide/unsafe-code-pointers/index).  
  
 Чтобы задать параметр unsafe в [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)], щелкните элемент **Проект** в главном меню, выберите область **Сборка** и установите флажок "разрешить небезопасный код".  
  
 В следующем примере при компиляции без **\/unsafe** создается ошибка CS0227:  
  
```  
// CS0227.cs public class MyClass { unsafe public static void Main()   // CS0227 { } }  
```  
  
## См. также  
 [C\# Compiler Errors](/dotnet/csharp/language-reference/compiler-messages/index)