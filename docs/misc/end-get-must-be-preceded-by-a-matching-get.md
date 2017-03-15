---
title: "Оператору End Get должен предшествовать соответствующий оператор Get | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30630"
  - "vbc30630"
helpviewer_keywords: 
  - "BC30630"
ms.assetid: d858076a-9088-4ad0-9766-95029476bf9b
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Оператору End Get должен предшествовать соответствующий оператор Get
Оператор `End Get` используется для завершения процедур свойств `Get`. Конструкция `End Get` обнаружена вне процедуры свойства `Get`.  
  
 **Идентификатор ошибки:** BC30630  
  
### Исправление ошибки  
  
1.  Убедитесь в том, что объявление процедуры свойства `Get` располагается после ключевого слова `Property` и перед конструкцией `End Property`.  
  
2.  Убедитесь в том, что процедура свойства `Get` начинается с ключевого слова `Get` и заканчивается конструкцией `End Get`.  
  
## См. также  
 [Оператор Property](/dotnet/visual-basic/language-reference/statements/property-statement)   
 [Property Changes in Visual Basic](http://msdn.microsoft.com/ru-ru/1c138efa-9bc2-44d7-80a0-f3a7c2510264)