---
title: "default может использоваться в операторе switch только один раз | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT1027"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: a94100f4-6ee5-4759-b635-9d309e47111e
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# default может использоваться в операторе switch только один раз
Предпринята попытка многократного использования оператора **default** в пределах оператора switch.  Вариант по умолчанию всегда является последним оператором варианта в операторе switch \(проходной вариант\).  
  
### Исправление ошибки  
  
-   Удалите все лишние операторы варианта **default** из оператора `switch` \(в операторе switch можно использовать не более одного варианта по умолчанию\).  
  
## См. также  
 [Оператор switch](../../javascript/reference/switch-statement-javascript.md)   
 [Управление выполнением программы](../../javascript/controlling-program-flow-javascript.md)   
 [Зарезервированные слова языка JavaScript](../../javascript/reference/javascript-reserved-words.md)