---
title: "Перегрузка методов, объявленных в нескольких интерфейсах базового класса, является недопустимой | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31410"
  - "vbc31410"
helpviewer_keywords: 
  - "BC31410"
ms.assetid: 7d1831c2-837c-4b02-8492-d0fc038fe184
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Перегрузка методов, объявленных в нескольких интерфейсах базового класса, является недопустимой
Несколько наследуемых интерфейсов неявно перегружают один и тот же метод.  
  
 **Идентификатор ошибки:** BC31410  
  
### Исправление ошибки  
  
-   Используйте модификатор `Shadows` вместо модификатора `Overloads`.  
  
## См. также  
 [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads)   
 [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows)