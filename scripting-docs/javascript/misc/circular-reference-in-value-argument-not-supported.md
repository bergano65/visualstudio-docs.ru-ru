---
title: "Циклические ссылки не поддерживаются в аргументах значений | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5034"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 5d06f0fa-86f5-49d1-8d50-af1759990f43
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Циклические ссылки не поддерживаются в аргументах значений
Была предпринята попытка вызова `JSON.stringify` с недопустимым значением.  Аргумент `value`, массив или объект содержат циклическую ссылку.  
  
### Чтобы исправить эту ошибку  
  
-   Удалите циклическую ссылку из аргумента.  
  
## Пример  
 В этом примере код вызывает ошибку во время выполнения, поскольку `john` содержит ссылку на `mary` и `mary` содержит ссылку на `john`.  Чтобы удалить циклическую ссылку, или удалите, или не устанавливайте свойство `brother` в объекте `mary` или свойство `sister` из объекта `john`.  
  
```javascript  
var john = new Object();  
var mary = new Object();  
john.sister = mary;  
mary.brother = john;  
  
// This line causes a runtime error.  
var error = JSON.stringify(john);  
```  
  
## См. также  
 [Объект JSON](../../javascript/reference/json-object-javascript.md)   
 [Функция JSON.parse](../../javascript/reference/json-parse-function-javascript.md)   
 [Ошибки времени выполнения JavaScript](../../javascript/reference/javascript-run-time-errors.md)