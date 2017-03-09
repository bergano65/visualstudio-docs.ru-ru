---
title: "Предупреждение компилятора (уровень&#160;1) CS0657 | Microsoft Docs"
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
  - "CS0657"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0657"
ms.assetid: d12d2efc-f44e-40e6-b825-5a66ead0c08e
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Предупреждение компилятора (уровень&#160;1) CS0657
"модификатор атрибута" не является допустимым местоположением атрибута в этом объявлении. Допустимыми для этого объявления являются местоположения "расположения". Все атрибуты в данном блоке будут игнорироваться.  
  
 Компилятором обнаружен модификатор атрибута в недопустимом положении. Дополнительные сведения см. в разделе [Целевые объекты атрибутов](http://msdn.microsoft.com/ru-ru/59a261f0-1cfb-4aa5-b610-6b735389882c).  
  
 При компиляции следующего примера будет выдано предупреждение CS0657:  
  
```  
// CS0657.cs // compile with: /target:library public class TestAttribute : System.Attribute {} [return: Test]   // CS0657 return not valid on a class class Class1 {}  
```