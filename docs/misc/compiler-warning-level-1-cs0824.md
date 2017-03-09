---
title: "Предупреждение компилятора (уровень&#160;1) CS0824 | Microsoft Docs"
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
  - "CS0824"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0824"
ms.assetid: ad643bb7-51b2-455b-a9f3-2bd4588d2c5d
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Предупреждение компилятора (уровень&#160;1) CS0824
Конструктор "имя" помечен как внешний.  
  
 Конструктор может быть помечен как extern \(внешний\). Однако компилятор не может проверить, существует ли этот конструктор в действительности. Поэтому создается предупреждение.  
  
### Удаление этого предупреждения  
  
1.  Используйте директиву pragma warning, чтобы игнорировать его.  
  
2.  Переместите конструктор в тип.  
  
## Пример  
 Следующий код приводит к возникновению ошибки CS0824:  
  
```  
// cs0824.cs public class C { extern C(); // CS0824 public static int Main() { return 1; } }  
```  
  
## См. также  
 [extern](/dotnet/csharp/language-reference/keywords/extern)   
 [\#pragma warning](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning)