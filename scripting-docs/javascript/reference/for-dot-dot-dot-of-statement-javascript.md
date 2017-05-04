---
title: "Оператор for...of (JavaScript) | Microsoft Docs"
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
ms.assetid: 7872b0b2-5701-4d72-9b52-ed13991542cc
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Оператор for...of (JavaScript)
Выполняет один или несколько операторов для каждого значения итератора, полученного от итерируемого объекта.  
  
## Синтаксис  
  
```  
for (variable of object) {  
    statements   
}  
```  
  
## Параметры  
 `variable`  
 Обязательный.  Переменная, которая может представлять значение любого свойства объекта `object`.  
  
 `object`  
 Обязательный.  Итерируемый объект, такой как `Array`, `Map`, `Set` или объект, реализующий [интерфейсы итератора](http://msdn.microsoft.com/ru-ru/3692355a-a703-4d43-8fb5-c03b4b7e8db1).  
  
 `statements`  
 Необязательный.  Один или несколько операторов, которые необходимо выполнять для каждого значения объекта `object`.  Может быть составным оператором.  
  
## Заметки  
 В начале каждой итерации цикла значение параметра `variable` имеет следующее значение свойства объекта `object`.  
  
## Пример  
 В следующем примере показано применение оператора `for...of` к массиву.  
  
```javascript  
let arr = [ "fred", "tom", "bob" ];  
  
for (let i of arr) {  
    console.log(i);  
}  
  
// Output:  
// fred  
// tom  
// bob  
  
```  
  
## Пример  
 В следующем примере показано применение оператора `for...of` к объекту `Map`.  
  
```javascript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
  
for (var n of m) {  
  console.log(n);  
}  
  
// Output:  
// 1,black  
// 2,red  
  
```  
  
## Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## См. также  
 [Оператор for...in](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [Оператор for](../../javascript/reference/for-statement-javascript.md)   
 [Оператор while](../../javascript/reference/while-statement-javascript.md)