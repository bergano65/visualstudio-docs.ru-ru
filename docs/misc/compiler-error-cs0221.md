---
title: "Ошибка компилятора CS0221 | Microsoft Docs"
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
  - "CS0221"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0221"
ms.assetid: 97170b49-54f1-4dac-a865-2f9cc6bf55b1
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0221
Постоянное значение "значение" не может быть преобразовано в "тип" \(для переопределения используйте синтаксис "unchecked"\)  
  
 В блоке [checked](/dotnet/csharp/language-reference/keywords/checked), включенном по умолчанию, обнаружена операция присваивания, которая может привести к потере данных. Чтобы устранить эту ошибку, исправьте операцию присвоения или используйте ключевое слово [unchecked](/dotnet/csharp/language-reference/keywords/unchecked). Для получения дополнительной информации см. [Checked и Unchecked](/dotnet/csharp/language-reference/keywords/checked-and-unchecked).  
  
 При компиляции следующего примера возникнет ошибка CS0221:  
  
```  
// CS0221.cs public class MyClass { public static void Main() { // unchecked // { int a = (int)0xFFFFFFFF;   // CS0221 a++; // } } }  
```