---
title: "Ограничение Class нельзя указывать несколько раз для одного параметра типа. | Microsoft Docs"
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
  - "bc32101"
  - "vbc32101"
helpviewer_keywords: 
  - "BC32101"
ms.assetid: fac2330a-e397-4bd9-8166-934407575f9e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Ограничение Class нельзя указывать несколько раз для одного параметра типа.
Список ограничений включает ограничение [Class \(Visual Basic\)](http://msdn.microsoft.com/ru-ru/0777c6e6-46bc-451b-ad70-57b49d4ef4f7) несколько раз.  
  
 Список ограничений в параметре типа может указывать, что аргумент типа, переданный в этот параметр типа, должен быть типом значения \(с ограничением [Structure &#91;Visual Basic&#93;](http://msdn.microsoft.com/ru-ru/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)\) или ссылочным типом \(с ограничением `Class`\). Нельзя указывать оба ограничения в одном и том же параметре типа, и нельзя указывать какое\-либо из них более одного раза.  
  
 Идентификатор ошибки: BC32101  
  
### Исправление ошибки  
  
-   Удалите все избыточные ключевые слова `Class`. В списке ограничений должно быть только одно ключевое слово.  
  
## См. также  
 [Универсальные типы в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Типы значений и ссылочные типы](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)