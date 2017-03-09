---
title: "Вызов конструктора допустим только как первый оператор в конструкторе экземпляра | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30282"
  - "bc30282"
helpviewer_keywords: 
  - "BC30282"
ms.assetid: c51b172f-fbd7-4ef5-8276-01a4bf6ed35b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Вызов конструктора допустим только как первый оператор в конструкторе экземпляра
Вызов `New()` выполняется после первого оператора конструктора. Если один конструктор явно вызывает другой, он должен сделать это в первом операторе после оператора `Sub New()`.  
  
 **Идентификатор ошибки:** BC30282  
  
### Исправление ошибки  
  
-   Удалите вызов `New()` или переместите его в начало конструктора.  
  
## См. также  
 [НЕ В СБОРКЕ. Использование конструкторов и деструкторов](http://msdn.microsoft.com/ru-ru/548eebe1-86c4-4377-b2f5-447cb8be3d90)