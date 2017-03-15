---
title: "Оператор не может присутствовать в теле события | Microsoft Docs"
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
  - "bc31112"
  - "vbc31112"
helpviewer_keywords: 
  - "BC31112"
ms.assetid: fd51fc53-a008-4b79-85fb-2d9fa1fb5a79
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Оператор не может присутствовать в теле события
Оператор не может присутствовать в теле события. Предполагается конец события.  
  
 Оператор, недопустимый в теле события, находится в нем.  
  
 **Идентификатор ошибки:** BC31112  
  
### Исправление ошибки  
  
-   Добавьте `End Event` перед оператором.  
  
## См. также  
 [Application Events Sample](http://msdn.microsoft.com/ru-ru/289a787f-b97e-43c8-a304-fe95e45f4a0d)   
 [Оператор Event](/dotnet/visual-basic/language-reference/statements/event-statement)