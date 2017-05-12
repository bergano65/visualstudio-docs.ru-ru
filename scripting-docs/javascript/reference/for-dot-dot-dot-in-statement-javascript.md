---
title: "Оператор for...in (JavaScript) | Microsoft Docs"
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
helpviewer_keywords: 
  - "операторы итерации, оператор for...in"
  - "циклические структуры, операторы for...in"
ms.assetid: 1b51a0ce-89f7-4a69-88ed-017b47dc398f
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# Оператор for...in (JavaScript)
Выполняет один или несколько операторов для каждого свойства объекта или для каждого элемента массива.  
  
## Синтаксис  
  
```  
for (variable in [object | array]) {  
    statements   
}  
```  
  
## Параметры  
 `variable`  
 Обязательный.  Переменная, которая может представлять собой имя любого свойства `object` или индекс любого элемента `array`.  
  
 `object`, `array`  
 Необязательный.  Объект или массив, по которому выполняется итерация.  
  
 `statements`  
 Необязательный.  Один или несколько операторов, которые требуется выполнить для каждого свойства `object` или каждого элемента `array`.  Может представлять собой составную инструкцию.  
  
## Заметки  
 В начале каждой итерации цикла, значение `variable` представляет собой имя следующего свойства `object` или индекс следующего элемента `array`.  Затем можно использовать `variable` в любом из операторов внутри цикла для ссылки на свойство `object` или элемент `array`.  
  
 Свойства объекта не присваиваются каким\-либо определенным образом.  Нельзя указать конкретное свойство по его индексу, только по имени свойства.  
  
 Перебор массива выполняется в порядке элементов, т. е. 0, 1, 2.  
  
## Пример  
 В следующем примере показано использование оператора `for...in` для объекта, используемого в качестве ассоциативного массива.  
  
```javascript  
// Initialize object.  
a = {"a" : "Athens" , "b" : "Belgrade", "c" : "Cairo"}  
  
// Iterate over the properties.  
var s = ""  
for (var key in a) {  
    s += key + ": " + a[key];  
    s += "<br />";  
    }  
document.write (s);  
  
// Output:  
// a: Athens  
// b: Belgrade  
// c: Cairo  
```  
  
## Пример  
 В следующем примере показано использование оператора `for ... in` для итерации по объекту `Array`, имеющему свойства expando.  
  
```javascript  
// Initialize the array.  
var arr = new Array("zero","one","two");  
  
// Add a few expando properties to the array.  
arr["orange"] = "fruit";  
arr["carrot"] = "vegetable";  
  
// Iterate over the properties and elements.  
var s = "";  
for (var key in arr) {  
    s += key + ": " + arr[key];  
    s += "<br />";  
}  
  
document.write (s);  
  
// Output:  
//   0: zero  
//   1: one  
//   2: two  
//   orange: fruit  
//   carrot: vegetable  
```  
  
> [!NOTE]
>  Для итерации по элементам коллекции используется объект `Enumerator`.  
  
## Требования  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## См. также  
 [Оператор for](../../javascript/reference/for-statement-javascript.md)   
 [Оператор while](../../javascript/reference/while-statement-javascript.md)