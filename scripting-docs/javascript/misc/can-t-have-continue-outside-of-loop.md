---
title: "continue не может располагаться вне цикла | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT1020"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: d2d95259-b2bc-4069-9876-60c30ad600a3
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# continue не может располагаться вне цикла
Предпринята попытка использовать оператор **continue** вне цикла.  Оператор **continue** может использоваться только внутри тела:  
  
-   цикла `do-while`,  
  
-   цикла `while`,  
  
-   цикла **for**,  
  
-   цикла **for\/in**.  
  
### Исправление ошибки  
  
-   Убедитесь, что оператор **continue** используется внутри тела:  
  
    -   цикла `do-while`,  
  
    -   цикла `while`,  
  
    -   цикла **for**,  
  
    -   цикла **for\/in**.  
  
## См. также  
 [Оператор continue](../../javascript/reference/continue-statement-javascript.md)   
 [Управление выполнением программы](../../javascript/controlling-program-flow-javascript.md)   
 [Устранение неполадок скриптов](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)