---
title: "Ошибка компилятора CS1032 | Microsoft Docs"
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
  - "CS1032"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1032"
ms.assetid: fe318a6c-4403-4b9b-b3d8-753ec31c00ff
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1032
Невозможно определить символы препроцессора или отменить их определение где\-либо, кроме начала файла.  
  
 [Директивы препроцессора](/dotnet/csharp/language-reference/preprocessor-directives/index) `#define` и `#undef` необходимо использовать в начале программы, перед другими ключевыми словами, например используемыми в объявлении пространства имен.  
  
 В следующем примере возникает ошибка CS1032:  
  
```  
// CS1032.cs namespace x { public class clx { #define a   // CS1032, put before namespace public static void Main() { } } }  
```