---
title: "Функция Promise.race (Promise) | Microsoft Docs"
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
ms.assetid: 9236eced-d313-4d03-8c3e-d89d762b3084
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Функция Promise.race (Promise)
Создает новый объект Promise, который будет разрешен или отклонен с тем же значением результата, что и первый разрешенный или отклоненный объект Promise в числе переданных аргументов.  
  
## Синтаксис  
  
```  
Promise.race(iterable)  
  
```  
  
#### Параметры  
 `iterable`  
 Обязательный.  Один или несколько объектов Promise.  
  
## Заметки  
 Если один из объектов Promise в объекте `iterable` уже разрешен или отклонен, `Promise.race` возвращает разрешенный или отклоненный объект Promise в том же виде, а результирующее значение равно значению, которое использовалось для разрешения \(или отклонения\) этого объекта.  Если в объекте `iterable` разрешены или отклонены уже несколько объектов Promise, `Promise.race` возвращает объект Promise, разрешенный таким же образом, как и первый итерированный объект Promise.  Если итерируемый объект не содержит разрешенных или отклоненных объектов Promise, объект Promise, возвращенный из `Promise.race`, также не разрешается и не отклоняется.  
  
## Пример  
  
```javascript  
var p1 = new Promise(function(resolve, reject) {  
    setTimeout(resolve, 0, 'success');  
});  
var p2 = new Promise(function(resolve, reject) { });  
var p2 = new Promise(function(resolve, reject) { });  
  
var race = Promise.race( [p1, p2, p3] );  
race.then(function(result) {  
    console.log(result);  
});  
  
// Output:  
// success  
  
var race = Promise.race( [Promise.reject('failure'),  
    Promise.resolve('success')] );  
race.catch(function(result) {  
    console.log(result);  
});  
  
// Output:  
// failure  
  
```  
  
## Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## См. также  
 [Объект Promise](../../javascript/reference/promise-object-javascript.md)