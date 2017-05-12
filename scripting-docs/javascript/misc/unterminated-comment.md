---
title: "Комментарий без признака завершения | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT1016"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: d4286315-814b-4966-b4c4-1ee19d796eff
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Комментарий без признака завершения
Отсутствует необходимое завершение начатого блока многострочного комментария.  Комментарии, состоящие из нескольких строк, должны начинаться с комбинации знаков "\/\*", а заканчиваться обратной комбинацией "\*\/".  Ниже представлен пример.  
  
```javascript  
/* This is a comment  
This is another part of the same comment.*/  
```  
  
### Исправление ошибки  
  
-   Обязательно завершайте комментарии, состоящие из нескольких строк, комбинацией знаков "\*\/".  
  
## См. также  
 [Операторы комментария](../../javascript/reference/comment-statements-javascript.md)