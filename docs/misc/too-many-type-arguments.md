---
title: "Слишком много аргументов типа | Microsoft Docs"
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
  - "vbc36579"
  - "bc36579"
helpviewer_keywords: 
  - "BC36579"
ms.assetid: f59617b2-ca66-45c6-baaa-3c8bdf7f9a55
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Слишком много аргументов типа
Универсальный метод был вызван с большим числом аргументов типа, чем число параметров типа.  
  
 При вызове универсального метода вы должны предоставить по одному аргументу типа для каждого параметра типа, определяемого этим методом.  
  
 **Идентификатор ошибки:** BC36579  
  
### Исправление ошибки  
  
-   Удалите аргументы типа из списка аргументов типа так, чтобы имелось по одному аргументу типа для каждого параметра типа в вызываемом универсальном методе.  
  
## См. также  
 [Универсальные типы в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Список типов](/dotnet/visual-basic/language-reference/statements/type-list)