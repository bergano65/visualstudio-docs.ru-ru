---
title: "Определение &quot;AddHandler&quot; отсутствует для события &quot;&lt;имя_события&gt;&quot; | Microsoft Docs"
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
  - "bc31130"
  - "vbc31130"
helpviewer_keywords: 
  - "BC31130"
ms.assetid: cf6c7fd6-ce2e-4916-b427-2a4a63e7279d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Определение &quot;AddHandler&quot; отсутствует для события &quot;&lt;имя_события&gt;&quot;
Если событие объявляется как `Custom`, то оно должно предоставлять процедуру для добавления обработчика событий.  
  
 **Идентификатор ошибки:** BC31130  
  
### Исправление ошибки  
  
1.  Включите объявление `AddHandler` между операторами `Custom Event` и `End Event`.  
  
2.  Проверьте правильность завершения других процедур в объявлении события.  
  
## См. также  
 [Оператор AddHandler](/dotnet/visual-basic/language-reference/statements/addhandler-statement)   
 [Оператор Event](/dotnet/visual-basic/language-reference/statements/event-statement)