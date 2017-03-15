---
title: "Оператор не может присутствовать в теле интерфейса | Microsoft Docs"
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
  - "vbc30603"
  - "BC30603"
helpviewer_keywords: 
  - "BC30603"
ms.assetid: 3aef29d6-eadf-4f1f-b214-dfeae5e51c4f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Оператор не может присутствовать в теле интерфейса
Объявление члена интерфейса включает оператор его завершения в виде `End` *имя\_члена*.  
  
 Интерфейс определяет только сигнатуру своих членов. Следовательно, у процедур и свойств, определенных в интерфейсе, есть только исходная строка, определяющая имя и сигнатуру. Не следует включать в интерфейс какой\-либо код, внутренние объявления или операторы `End Function`, `End Property` и `End Sub`.  
  
 **Идентификатор ошибки:** BC30603  
  
### Исправление ошибки  
  
-   Удалите оператор `End` *имя\_члена* из определения интерфейса.  
  
## См. также  
 [Оператор Interface](/dotnet/visual-basic/language-reference/statements/interface-statement)   
 [Оператор End \<ключевое\_слово\>](../Topic/End%20%3Ckeyword%3E%20Statement%20\(Visual%20Basic\).md)