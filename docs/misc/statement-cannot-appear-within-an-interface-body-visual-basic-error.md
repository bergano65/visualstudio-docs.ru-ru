---
title: "Оператор не может присутствовать в теле интерфейса (ошибка Visual Basic) | Microsoft Docs"
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
  - "bc30604"
  - "vbc30604"
helpviewer_keywords: 
  - "BC30604"
ms.assetid: ce4759fe-5e49-43ad-8405-a3f46ed0a36f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Оператор не может присутствовать в теле интерфейса (ошибка Visual Basic)
Обнаружена непредвиденная конструкция языка. Предполагается, что конструкция `End Interface` пропущена и что весь последующий исходный код находится за пределами интерфейса.  
  
 **Идентификатор ошибки:** BC30604  
  
### Исправление ошибки  
  
1.  Проверьте синтаксис кода в определении интерфейса.  
  
2.  Убедитесь в том, что определение интерфейса заканчивается конструкцией `End Interface`.  
  
## См. также  
 [Интерфейсы](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)   
 [Оператор Interface](/dotnet/visual-basic/language-reference/statements/interface-statement)