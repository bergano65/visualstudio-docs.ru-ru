---
title: "New не может использоваться в классе, объявленном как MustInherit. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30569"
  - "bc30569"
helpviewer_keywords: 
  - "BC30569"
ms.assetid: 94c9e6a3-6489-4d58-b7e5-7b4203677e3b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# New не может использоваться в классе, объявленном как MustInherit.
Класс `MustInherit` нельзя создать напрямую, и поэтому оператор `New` не может использоваться в классе `MustInherit`. Хотя можно иметь переменные и значения, типы времени компиляции которых являются `MustInherit`, такие переменные и значения обязательно иметь значение null или содержать ссылки на экземпляры обычных классов, производных от типов `MustInherit`.  
  
 **Идентификатор ошибки:** BC30569  
  
### Исправление ошибки  
  
-   Удалите оператор `New`.  
  
## См. также  
 [MustInherit](/dotnet/visual-basic/language-reference/modifiers/mustinherit)   
 [Оператор New](/dotnet/visual-basic/language-reference/operators/new-operator)