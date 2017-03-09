---
title: "Слишком мало аргументов типа для &quot;&lt;genericMethodName&gt;&quot; | Microsoft Docs"
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
  - "bc32042"
  - "vbc32042"
helpviewer_keywords: 
  - "BC32042"
ms.assetid: e887b068-4e84-4cb4-9649-94fe162a821e
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Слишком мало аргументов типа для &quot;&lt;genericMethodName&gt;&quot;
Универсальный метод был вызван с меньшим числом аргументов типа, чем число параметров типа.  
  
 При вызове универсального метода вы должны предоставить по одному аргументу типа для каждого параметра типа, определяемого этим методом.  
  
 **Идентификатор ошибки:** BC32042  
  
### Исправление ошибки  
  
-   Добавьте аргументы типа в список аргументов типа так, чтобы имелось по одному аргументу типа для каждого параметра типа в вызываемом универсальном методе.  
  
## См. также  
 [Универсальные типы в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Список типов](/dotnet/visual-basic/language-reference/statements/type-list)   
 [Универсальные процедуры в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)