---
title: "Ожидался символ &quot;(&quot; (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT1005"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 712315e1-4c68-4f66-84c2-41b83c42d85a
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Ожидался символ &quot;(&quot; (JavaScript)
Предпринята попытка заключить выражение в круглые скобки, но открывающая скобка не поставлена.  Некоторые выражения должны быть заключены в круглые скобки \(открывающие и закрывающие\).  Обратите внимание на использование круглых скобок в следующем примере.  
  
```javascript  
for (initialize; test; increment) {  
statement;  
}  
```  
  
### Исправление ошибки  
  
-   Добавьте левую скобку в выражение вычисления.