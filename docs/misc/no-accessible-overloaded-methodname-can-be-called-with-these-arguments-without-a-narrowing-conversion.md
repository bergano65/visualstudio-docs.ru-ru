---
title: "Ни один из доступных перегруженных &quot;&lt;имя_метода&gt;&quot; не может вызываться с этими аргументами без преобразования с сужением | Microsoft Docs"
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
  - "vbrAmbiguousMatch_NarrowingConversion1"
ms.assetid: 2fdbadb9-8ef1-404a-a2ed-ce5f5e55cfcb
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Ни один из доступных перегруженных &quot;&lt;имя_метода&gt;&quot; не может вызываться с этими аргументами без преобразования с сужением
Вызван перегруженный метод, однако ни один метод не может быть сопоставлен со списком предоставленных аргументов без сужающего преобразования.  
  
### Исправление ошибки  
  
1.  Задайте имя `Option Strict Off`.  
  
2.  Измените аргументы таким образом, чтобы они соответствовали одной из сигнатур перегруженного метода.  
  
## См. также  
 [Передача аргументов по значению и по ссылке](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference)   
 [Расширяющие и сужающие преобразования](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)