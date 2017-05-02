---
title: "Число цифр дробной части вне диапазона | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5026"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: dbe05d7d-fcf6-4823-9c61-4b814d1ad3c4
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Число цифр дробной части вне диапазона
Предпринята попытка передать недопустимый аргумент в функцию **Number.prototype.toExponential**.  Аргумент функции **toExponential\(\)** должен иметь значение в диапазоне от 0 до 20 \(включительно\).  
  
### Исправление ошибки  
  
-   Убедитесь, что значение аргумента **toExponential\(\)** не является слишком большим или слишком маленьким.  
  
## См. также  
 [Метод toExponential \(Number\)](../../javascript/reference/toexponential-method-number-javascript.md)