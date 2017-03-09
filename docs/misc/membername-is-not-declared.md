---
title: "&quot;&lt;имя_члена&gt;&quot; не объявлен | Microsoft Docs"
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
  - "vbc30816"
  - "bc30816"
helpviewer_keywords: 
  - "BC30816"
ms.assetid: d6704bed-bb76-47c6-ac28-09608d5e6912
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;&lt;имя_члена&gt;&quot; не объявлен
"`<membername>`" не объявлен. Возможности `Debug` доступны в пространстве имен `System.Diagnostics.Debug` сборки `System`.  
  
 Член с указанным именем не найден.  
  
 **Идентификатор ошибки:** BC30816  
  
### Исправление ошибки  
  
1.  Проверьте правильность написания имени члена.  
  
2.  Используйте оператор `Imports` или укажите полные имена для членов, объявленных в других пространствах имен. Например, функция `WriteLine` объявлена в пространстве имен `System.Diagnostics.Debug`.  
  
## См. также  
 [Отладка в Visual Studio](../debugger/debugging-in-visual-studio.md)