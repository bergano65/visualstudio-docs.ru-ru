---
title: "Функция Promise.reject (Promise) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 9746e15b-9717-4e36-bf6b-910dcc6cd667
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Функция Promise.reject (Promise)
Создает новый отклоненный объект Promise с результатом, равным переданному аргументу.  
  
## Синтаксис  
  
```  
Promise.reject(r);  
```  
  
#### Параметры  
 `r`  
 Обязательный.  Причина отклонения объекта Promise.  
  
## Заметки  
 Функция обработки ошибок метода `then` или `catch` выполняется при возвращении отклоненного объекта Promise.  
  
## Пример  
  
```javascript  
var p = Promise.reject('failure');  
p.catch(function(result) {  
    console.log(result);  
});  
  
// Output:  
// failure  
```  
  
## Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## См. также  
 [Объект Promise](../../javascript/reference/promise-object-javascript.md)