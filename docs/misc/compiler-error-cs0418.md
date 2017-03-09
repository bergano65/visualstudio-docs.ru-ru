---
title: "Ошибка компилятора CS0418 | Microsoft Docs"
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
  - "CS0418"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0418"
ms.assetid: b78fafde-428b-4fa2-a933-c4614760bb71
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0418
"имя\_класса": абстрактный класс не может иметь тип sealed или static  
  
 Абстрактный класс не может использоваться для создания объектов, если он не является производным, поэтому нет смысла делать его запечатанным. Абстрактный класс также не имеет смысла делать статическим; абстрактные классы предназначены для поддержки иерархии объектов, которая будет использовать абстрактный класс в качестве основы.  
  
## Пример  
 В следующем примере возникает ошибка CS0418:  
  
```  
// CS0418.cs public abstract sealed class C  // CS0418 { } sealed static class S  // CS0418 { } public class MyClass { public static void Main() { } }  
```