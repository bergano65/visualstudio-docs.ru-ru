---
title: "Ожидалось ключевое слово &quot;catch&quot; | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT1033"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: f1cd947f-eba2-411e-8e84-8ca86f608643
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Ожидалось ключевое слово &quot;catch&quot;
Использован блок обработки исключений **try**, но не написан связанный с ним оператор **catch**.  Механизм обработки исключений требует, чтобы код, который может завершиться ошибкой, вместе с кодом, который не должен выполняться при возникновении исключения, был помещен внутрь блока **try**.  Исключения создаются внутри блока **try** с помощью оператора **throw** и перехватываются вне блока **try** с помощью одного или нескольких операторов **catch**.  
  
### Исправление ошибки  
  
-   Добавьте соответствующий блок **catch**.  
  
-   Попробуйте использовать блок **finally** вместо блока **catch**.  
  
## См. также  
 [Оператор try...catch...finally](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Объект Error](../../javascript/reference/error-object-javascript.md)