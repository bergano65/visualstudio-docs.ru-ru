---
title: "Методы &quot;&lt;метод1&gt;&quot; и &quot;&lt;метод2&gt;&quot; не могут перегружать друг друга, так как они отличаются только параметрами, объявленными как ParamArray | Microsoft Docs"
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
  - "bc30368"
  - "vbc30368"
helpviewer_keywords: 
  - "BC30368"
ms.assetid: 6111df0c-fc3e-40b2-b536-effbd132ef72
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Методы &quot;&lt;метод1&gt;&quot; и &quot;&lt;метод2&gt;&quot; не могут перегружать друг друга, так как они отличаются только параметрами, объявленными как ParamArray
Предпринята попытка перегрузки двух методов, которые отличаются друг от друга только параметром или параметрами `ParamArray`. Компилятор считает, что процедура с параметром `ParamArray` имеет бесконечное число перегрузок, отличающихся друг от друга тем, что передается в массив параметров.  
  
 **Идентификатор ошибки:** BC30368  
  
### Исправление ошибки  
  
-   Убедитесь, что методы отличаются друг от друга не только параметрами `ParamArray`.  
  
## См. также  
 [Вопросы, связанные с перегрузкой процедур](/dotnet/visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures)   
 [Массивы параметров](/dotnet/visual-basic/programming-guide/language-features/procedures/parameter-arrays)