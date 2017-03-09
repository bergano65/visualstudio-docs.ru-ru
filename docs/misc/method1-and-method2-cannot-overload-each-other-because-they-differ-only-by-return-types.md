---
title: "Методы &quot;&lt;метод1&gt;&quot; и &quot;&lt;метод2&gt;&quot; не могут перегружать друг друга, так как они отличаются только типами возврата | Microsoft Docs"
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
  - "bc30301"
  - "vbc30301"
helpviewer_keywords: 
  - "BC30301"
ms.assetid: 5adc442b-9671-4d93-add8-42929b1a09b9
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Методы &quot;&lt;метод1&gt;&quot; и &quot;&lt;метод2&gt;&quot; не могут перегружать друг друга, так как они отличаются только типами возврата
Предпринята попытка перегрузки одного метода другим, отличающимся от первого только типом возврата. При перегрузке любые две версии метода должны отличаться списками аргументов; для различения методов вы можете использовать только списки аргументов.  
  
 **Идентификатор ошибки:** BC30301  
  
### Исправление ошибки  
  
-   Убедитесь, что методы отличаются списками аргументов.  
  
## См. также  
 [Перегрузка процедур](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-overloading)   
 [Вопросы, связанные с перегрузкой процедур](/dotnet/visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures)