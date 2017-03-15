---
title: "&quot;&lt;спецификатор&gt;&quot; недопустим в объявлении события интерфейса | Microsoft Docs"
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
  - "bc30275"
  - "vbc30275"
helpviewer_keywords: 
  - "BC30275"
ms.assetid: bd12c952-c619-4753-8d6d-90ef4086fdc2
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;&lt;спецификатор&gt;&quot; недопустим в объявлении события интерфейса
Оператор `Event` в интерфейсе содержит ключевое слово, которое не разрешено, например `Implements`. Интерфейс может только определять члены, но не реализовывать их.  
  
 **Идентификатор ошибки:** BC30275  
  
### Исправление ошибки  
  
1.  Удалите это ключевое слово из объявления.  
  
2.  Переместите реализацию членов интерфейса в класс, реализующий интерфейс.  
  
## См. также  
 [Оператор Interface](/dotnet/visual-basic/language-reference/statements/interface-statement)   
 [Оператор Implements](/dotnet/visual-basic/language-reference/statements/implements-statement)