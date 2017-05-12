---
title: "Точность вне диапазона | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5027"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: c16760ac-fc08-49d7-8878-9bc434b3c080
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Точность вне диапазона
Предпринята попытка передать недопустимый аргумент функции **Number.prototype.toPrecision**.  Аргумент **toPrecision** должен иметь значение от 1 до 21 \(включительно\).  
  
### Исправление ошибки  
  
-   Убедитесь, что аргумент `toPrecision` не имеет слишком большое или слишком маленькое значение.  
  
## См. также  
 [Метод toPrecision \(Number\)](../../javascript/reference/toprecision-method-number-javascript.md)