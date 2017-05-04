---
title: "Функция Promise.all (Promise) | Microsoft Docs"
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
ms.assetid: 02a7b90c-96f6-4484-9466-d261efa1b494
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Функция Promise.all (Promise)
Соединяет два или более объекта Promise и возвращает значение только после завершения или отклонения всех этих объектов.  
  
## Синтаксис  
  
```  
Promise.all(func1, func2 [,funcN])  
```  
  
#### Параметры  
 `func1`  
 Обязательный.  Функция, которая возвращает объект Promise.  
  
 `func2`  
 Обязательный.  Функция, которая возвращает объект Promise.  
  
 `funcN`  
 Необязательный.  Одна или несколько функций, которые возвращают объект Promise.  
  
## Заметки  
 Возвращаемый результат представляет собой массив значений, возвращенных завершенными объектами Promise.  Если какой\-либо из объединяемых объектов Promise отклоняется, функция `Promise.all` возвращает причину отклонения \(все остальные возвращенные значения не учитываются\).  
  
## Пример  
 В данном коде первый вызов функции timeout возвращает значение через 5 000 мс.  Обработчик завершения вызывает функцию `Promise.all`, которая возвращает значение только после того, как оба вызова функции timeout будут завершены или отклонены.  
  
```javascript  
function timeout(duration) {  
    return new Promise(function(resolve, reject) {  
        setTimeout(resolve, duration);  
    });  
}  
  
var p = timeout(5000).then(() => {  
    return Promise.all([timeout(100), timeout(200)]);  
})  
```  
  
## Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## См. также  
 [Объект Promise](../../javascript/reference/promise-object-javascript.md)