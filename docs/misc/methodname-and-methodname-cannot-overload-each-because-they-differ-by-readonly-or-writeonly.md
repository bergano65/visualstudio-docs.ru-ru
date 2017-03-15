---
title: "Методы &quot;&lt;имя_метода&gt;&quot; и &quot;&lt;имя_метода&gt;&quot; не могут перегружать друг друга, так как они отличаются только по ReadOnly или WriteOnly. | Microsoft Docs"
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
  - "vbc30366"
  - "BC30366"
helpviewer_keywords: 
  - "BC30366"
ms.assetid: 2440fd29-e205-4004-b2ee-9d954d17b8d3
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Методы &quot;&lt;имя_метода&gt;&quot; и &quot;&lt;имя_метода&gt;&quot; не могут перегружать друг друга, так как они отличаются только по ReadOnly или WriteOnly.
Предпринята попытка перегрузки двух методов, которые отличаются друг от друга только в их объявлениях `ReadOnly` и `WriteOnly`. Для различения версий нельзя использовать ничего, кроме списка аргументов.  
  
 **Идентификатор ошибки:** BC30366  
  
### Исправление ошибки  
  
-   Убедитесь, что методы отличаются друг от друга не только `ReadOnly` и `WriteOnly`.  
  
## См. также  
 [Вопросы, связанные с перегрузкой процедур](/dotnet/visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures)