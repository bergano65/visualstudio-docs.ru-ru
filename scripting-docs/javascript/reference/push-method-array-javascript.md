---
title: "Метод push (Array) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "push"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Push - метод"
ms.assetid: fa6e5799-dabe-4b3d-bd1f-0afc68c77134
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Метод push (Array) (JavaScript)
Добавляет новые элементы к массиву и возвращает новую длину массива.  
  
## Синтаксис  
  
```  
  
arrayObj.push([item1 [item2 [. . . [itemN ]]]])  
```  
  
## Параметры  
 `arrayObj`  
 Обязательный.  Объект `Array`.  
  
 `item, item2,. . ., itemN`  
 Необязательный.  Новые элементы объекта `Array`.  
  
## Заметки  
 Методы `push` и `pop` позволяют моделировать стек типа LIFO.  
  
 Метод `push` добавляет элементы в порядке их следования.  Если один из аргументов является массивом, он добавляется как один элемент.  Для объединения элементов из нескольких массивов используется метод `concat`.  
  
## Пример  
 В следующем примере показано использование метода `push`.  
  
```javascript  
var number;  
var my_array = new Array();  
  
my_array.push (5, 6, 7);  
my_array.push (8, 9);  
  
number = my_array.pop();  
while (number != undefined)  
   {  
   document.write (number + " ");  
   number = my_array.pop();  
   }  
  
// Output:  
// 9 8 7 6 5  
```  
  
## Требования  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## См. также  
 [Метод concat \(массив\)](../../javascript/reference/concat-method-array-javascript.md)   
 [Метод pop \(Array\)](../../javascript/reference/pop-method-array-javascript.md)