---
title: "Доступ к свойству должен выполняться для присваивания или считывания его значения | Microsoft Docs"
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
  - "bc30545"
  - "vbc30545"
helpviewer_keywords: 
  - "BC30545"
ms.assetid: df271c05-1e7a-44e8-bf53-79f06ef916ab
caps.latest.revision: 11
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Доступ к свойству должен выполняться для присваивания или считывания его значения
Предпринята попытка доступа к свойству без присваивания ему значения или использования его значения. Примером является следующий код:  
  
 [!CODE [VbVbalrErrorSamples#1](VbVbalrErrorSamples#1)]  
  
 **Идентификатор ошибки:** BC30545  
  
### Исправление ошибки  
  
-   Присвойте значение свойству, как показано в следующем примере:  
  
     [!CODE [VbVbalrErrorSamples#3](VbVbalrErrorSamples#3)]  
  
     \-или\-  
  
-   Используйте значение свойства, как показано в следующем примере:  
  
     [!CODE [VbVbalrErrorSamples#2](VbVbalrErrorSamples#2)]  
  
## См. также  
 [Процедуры свойств](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [Операторы присваивания](/dotnet/visual-basic/language-reference/operators/assignment-operators)