---
title: "Предупреждение компилятора (уровень 1) CS3022 | Microsoft Docs"
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
  - "CS3022"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3022"
ms.assetid: 9340645c-10c3-4e21-a825-3f05fae02ff7
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Предупреждение компилятора (уровень 1) CS3022
Атрибут CLSCompliant не имеет значения при применении к параметрам Попробуйте поместить его в методе.  
  
 Параметры метода не проверяются на CLS\-совместимость, поскольку правила CLS\-совместимости применяются к методам и объявлениям типов.  
  
## Пример  
 В следующем примере возникает ошибка CS3022:  
  
```  
// CS3022.cs // compile with: /W:1 using System; [assembly: CLSCompliant(true)] [CLSCompliant(true)] public class C { public void F([CLSCompliant(true)] int i) { } public static void Main() { } }  
```