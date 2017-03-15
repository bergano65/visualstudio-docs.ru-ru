---
title: "В структуре &quot;&lt;имя_структуры&gt;&quot; должна содержаться по меньшей мере одна переменная-член экземпляра или одно объявление события | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30281"
  - "vbc30281"
helpviewer_keywords: 
  - "BC30281"
ms.assetid: a03ee4e2-5fea-4933-898f-7f125b25824e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# В структуре &quot;&lt;имя_структуры&gt;&quot; должна содержаться по меньшей мере одна переменная-член экземпляра или одно объявление события
Обнаружена функционально пустая структура. Между оператором `Structure` и оператором `End Structure` должен быть объявлен по крайней мере один член\-переменная.  
  
 **Идентификатор ошибки:** BC30281  
  
### Исправление ошибки  
  
-   Добавьте оператор `Dim` или `Event` в структуру.  
  
## См. также  
 [Оператор Structure](/dotnet/visual-basic/language-reference/statements/structure-statement)   
 [Оператор Dim](/dotnet/visual-basic/language-reference/statements/dim-statement)   
 [Оператор Event](/dotnet/visual-basic/language-reference/statements/event-statement)