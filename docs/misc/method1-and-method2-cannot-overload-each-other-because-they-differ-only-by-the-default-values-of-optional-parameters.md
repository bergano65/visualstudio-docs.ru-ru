---
title: "Методы &quot;&lt;метод1&gt;&quot; и &quot;&lt;метод2&gt;&quot; не могут перегружать друг друга, так как они отличаются только значениями по умолчанию необязательных параметров | Microsoft Docs"
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
  - "vbc30305"
  - "bc30305"
helpviewer_keywords: 
  - "BC30305"
ms.assetid: f07f925e-9f95-4885-bdba-eaba2d0483d8
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Методы &quot;&lt;метод1&gt;&quot; и &quot;&lt;метод2&gt;&quot; не могут перегружать друг друга, так как они отличаются только значениями по умолчанию необязательных параметров
Предпринята попытка перегрузки одного метода другим, отличающимся от первого только необязательными параметрами. Метод с необязательным параметром эквивалентен двум перегруженным методам: одному с необязательным параметром и другому — без него. Таким образом, невозможно перегрузить метод со списком аргументов, соответствующим любому из этих вариантов.  
  
 **Идентификатор ошибки:** BC30305  
  
### Исправление ошибки  
  
-   Убедитесь, что методы отличаются друг от друга не только необязательными параметрами.  
  
## См. также  
 [Перегрузка процедур](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-overloading)   
 [Вопросы, связанные с перегрузкой процедур](/dotnet/visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures)