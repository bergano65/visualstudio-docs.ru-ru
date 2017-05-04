---
title: "Функция Promise.resolve (Promise) | Microsoft Docs"
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
ms.assetid: 0fb6bff9-54ab-41be-97d7-04f7e6fe9cff
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Функция Promise.resolve (Promise)
Создает новый разрешенный объект Promise с результатом, равным его аргументу.  
  
## Синтаксис  
  
```  
Promise.resolve(x)  
```  
  
#### Параметры  
 `x`  
 Обязательный.  Значение, возвращаемое с завершенным объектом Promise.  
  
## Заметки  
 Функция обработки исполнения метода `then` выполняется при возвращении завершенного объекта Promise.  
  
## Пример  
  
```javascript  
var p = Promise.resolve('success');  
p.then(function(result) {  
    console.log(result);  
});  
  
// Output:  
// success  
```  
  
## Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## См. также  
 [Объект Promise](../../javascript/reference/promise-object-javascript.md)