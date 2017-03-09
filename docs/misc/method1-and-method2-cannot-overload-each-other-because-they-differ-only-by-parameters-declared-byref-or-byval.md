---
title: "&quot;&lt;метод1&gt;&quot; и &quot;&lt;метод2&gt;&quot; не могут перегружать друг друга, так как они отличаются только параметрами, объявленными как &quot;ByRef&quot; или &quot;ByVal&quot; | Microsoft Docs"
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
  - "bc30345"
  - "vbc30345"
helpviewer_keywords: 
  - "BC30345"
ms.assetid: 82af13b1-2641-4881-b25a-c782974bded1
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;&lt;метод1&gt;&quot; и &quot;&lt;метод2&gt;&quot; не могут перегружать друг друга, так как они отличаются только параметрами, объявленными как &quot;ByRef&quot; или &quot;ByVal&quot;
Предпринята попытка перегрузки одного метода другим, отличающимся от первого только параметром, объявленным как `ByRef` или `ByVal`.  
  
 **Идентификатор ошибки:** BC30345  
  
### Исправление ошибки  
  
-   Убедитесь в том, что методы отличаются друг от друга не только параметром `ByRef` или `ByVal`.  
  
## См. также  
 [Перегрузка процедур](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-overloading)   
 [Вопросы, связанные с перегрузкой процедур](/dotnet/visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures)