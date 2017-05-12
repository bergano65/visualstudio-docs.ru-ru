---
title: "break не может располагаться вне цикла | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT1019"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 11d02172-2a78-4705-a730-d21111db5f42
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# break не может располагаться вне цикла
Предпринята попытка использовать ключевое слово **break** вне цикла.  Ключевое слово **break** используется для завершения цикла или оператора `switch`.  Оно должно быть внедрено в тело цикла или оператора `switch`.  Однако за ключевым словом break может следовать **метка**.  
  
```  
break labelname;  
```  
  
 При использовании вложенных циклов или операторов `switch`, когда необходимо прекратить цикл, который не является самым внутренним, необходимо использовать только ключевое слово **break** с меткой.  
  
### Исправление ошибки  
  
-   Убедитесь, что ключевое слово **break** находится внутри цикла или оператора switch.  
  
## См. также  
 [Оператор break](../../javascript/reference/break-statement-javascript.md)   
 [Управление выполнением программы](../../javascript/controlling-program-flow-javascript.md)   
 [Устранение неполадок скриптов](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)