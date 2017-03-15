---
title: "Ни один из доступных перегруженных &quot;&lt;имя_метода&gt;&quot; не может вызываться с этими аргументами без расширяющего преобразования: &lt;список&gt; | Microsoft Docs"
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
  - "vbrAmbiguousCall_WideningConversion2"
ms.assetid: 5e74f5cf-80bd-4b48-b58a-465f981ec694
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Ни один из доступных перегруженных &quot;&lt;имя_метода&gt;&quot; не может вызываться с этими аргументами без расширяющего преобразования: &lt;список&gt;
Вызван перегруженный метод, однако метод не может быть сопоставлен со списком указанных аргументов без расширяющего преобразования.  
  
### Исправление ошибки  
  
-   Задайте имя `Option Strict Off`.  
  
-   Измените аргументы таким образом, чтобы они соответствовали одной из сигнатур перегруженного метода.  
  
## См. также  
 [Расширяющие и сужающие преобразования](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)   
 [Оператор Option Strict](/dotnet/visual-basic/language-reference/statements/option-strict-statement)