---
title: "Определение &quot;RaiseEvent&quot; отсутствует для события &quot;&lt;имя_события&gt;&quot;. | Microsoft Docs"
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
  - "vbc31132"
  - "bc31132"
helpviewer_keywords: 
  - "BC31132"
ms.assetid: 8f3442fd-2ed1-4dbc-83a8-f0860ec022ac
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Определение &quot;RaiseEvent&quot; отсутствует для события &quot;&lt;имя_события&gt;&quot;.
Если событие объявляется как `Custom`, то оно должно предоставлять процедуру для вызова события.  
  
 **Идентификатор ошибки:** BC31132  
  
### Исправление ошибки  
  
1.  Включите объявление `RaiseEvent` между операторами `Custom Event` и `End Event`.  
  
2.  Проверьте правильность завершения других процедур в объявлении события.  
  
## См. также  
 [Оператор RaiseEvent](/dotnet/visual-basic/language-reference/statements/raiseevent-statement)   
 [Оператор Event](/dotnet/visual-basic/language-reference/statements/event-statement)