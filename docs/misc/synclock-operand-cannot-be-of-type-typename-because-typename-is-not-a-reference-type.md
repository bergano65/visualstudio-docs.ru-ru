---
title: "Операнд &quot;SyncLock&quot; не может иметь тип &quot;&lt;имя_типа&gt;&quot;, так как &quot;&lt;имя_типа&gt;&quot; не является ссылочным типом. | Microsoft Docs"
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
  - "vbc30582"
  - "bc30582"
helpviewer_keywords: 
  - "BC30582"
ms.assetid: 953aecf2-629a-4272-94bd-abf88f785e63
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Операнд &quot;SyncLock&quot; не может иметь тип &quot;&lt;имя_типа&gt;&quot;, так как &quot;&lt;имя_типа&gt;&quot; не является ссылочным типом.
Оператор `SyncLock` разрешает синхронизацию операторов в одном выражении, гарантируя, что одни и те же операторы не будут выполняться одновременно несколькими потоками. Тип выражения в операторе `SyncLock` должен быть ссылочным типом, таким как класс, модуль, интерфейс, массив или делегат.  
  
 **Идентификатор ошибки:** BC30582  
  
### Исправление ошибки  
  
-   Измените тип на соответствующий ссылочный тип.  
  
## См. также  
 [Оператор SyncLock](/dotnet/visual-basic/language-reference/statements/synclock-statement)   
 [НЕ В СБОРКЕ. Многопоточность в Visual Basic](http://msdn.microsoft.com/ru-ru/c731a50c-09c1-4468-9646-54c86b75d269)