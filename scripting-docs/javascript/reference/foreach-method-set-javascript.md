---
title: "Метод forEach (Set) (JavaScript) | Microsoft Docs"
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
ms.assetid: 813bff6e-6098-4260-ab6e-b0d2da6be94d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Метод forEach (Set) (JavaScript)
Выполняет указанное действие с каждым элементом в наборе.  
  
## Синтаксис  
  
```javascript  
setObj.forEach(callbackfn[, thisArg])  
```  
  
#### Параметры  
 `setObj`  
 Обязательное.  Объект `Set`.  
  
 `callbackfn`  
 Обязательное.  `callbackfn` принимает до трех аргументов.  Функция, которая вызывает `forEach` по одному разу для каждого элемента набора.  
  
 `thisArg`  
 Необязательный параметр.  Объект, на который может ссылаться ключевое слово `this` в функции `callbackfn`.  Если параметр `thisArg` опущен, `undefined` используется в качестве значения `this`.  
  
## Исключения  
 Если аргумент `callbackfn` не является объектом функции, вызывается исключение `TypeError`.  
  
## Заметки  
 Синтаксис функции обратного вызова таков:  
  
 `function callbackfn(value, key, setObj)`  
  
 Можно объявить функцию обратного вызова с помощью до 3 параметров, как показано в следующей таблице.  
  
|Аргумент обратного вызова|Определение|  
|-------------------------------|-----------------|  
|`value`|Значение, содержащееся в наборе.|  
|`key`|Значение, содержащееся в наборе.  Набор не содержит ключей, поэтому это значение совпадает с `value`.|  
|`setObj`|объект `Set` для прохождения.|  
  
## Пример  
 В следующем примере показано использование `forEach`.  Аргумент `callbackfn` содержит код для функции обратного вызова.  
  
```javascript  
var s = new Set();  
  
s.add("scale");  
s.add(10);  
s.add("5");  
  
s.forEach(function(item, sameItem, s) {  
    document.write("Size of the set object is: " + s.size + "<br />");  
    document.write("Deleting item: " + item + "<br />");  
    s.delete(sameItem);  
});  
  
// Output:  
// Size of the set object is: 3  
// Deleting item: scale  
// Size of the set object is: 2  
// Deleting item: 10  
// Size of the set object is: 1  
// Deleting item: 5  
```  
  
## Пример  
 В следующем примере показано, что можно также извлекать элементы из набора путем передачи только одного параметра функции обратного вызова.  
  
```javascript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
  
s.forEach(function (item) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776, founding father,  
  
```  
  
## Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]