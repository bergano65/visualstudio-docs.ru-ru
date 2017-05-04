---
title: "Метод forEach (Map) (JavaScript) | Microsoft Docs"
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
ms.assetid: 9cdf0adc-77c7-4407-8ba7-ada0fb09e507
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Метод forEach (Map) (JavaScript)
Выполняет указанное действие с каждым элементом в сопоставлении.  
  
## Синтаксис  
  
```javascript  
mapObj.forEach(callbackfn[, thisArg])  
```  
  
#### Параметры  
 `mapObj`  
 Обязательное.  Объект `Map`.  
  
 `callbackfn`  
 Обязательное.  Функция, которая вызывает `forEach` по одному разу для каждого элемента сопоставления.  `callbackfn` принимает до трех аргументов.  Метод `forEach` вызывает функцию `callbackfn` по одному разу для каждого элемента сопоставления.  
  
 `thisArg`  
 Необязательный параметр.  Объект, на который может ссылаться ключевое слово `this` в функции `callbackfn`.  Если параметр `thisArg` опущен, `undefined` используется в качестве значения `this`.  
  
## Исключения  
 Если аргумент `callbackfn` не является объектом функции, вызывается исключение `TypeError`.  
  
## Заметки  
 Синтаксис функции обратного вызова таков:  
  
 `function callbackfn(value, key, mapObj)`  
  
 Можно объявить функцию обратного вызова с помощью до 3 параметров, как показано в следующей таблице.  
  
|Аргумент обратного вызова|Определение|  
|-------------------------------|-----------------|  
|`value`|Значение, содержащееся в сопоставлении.|  
|`key`|Ключ, содержащиеся в сопоставлении.|  
|`mapObj`|объект `Map` для прохождения.|  
  
## Пример  
 В следующем примере показано, как извлечь члены `Map` с помощью `forEach`.  
  
```javascript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
m.set({x:1}, 3);  
  
m.forEach(function (item, key, mapObj) {  
    document.write(item.toString() + "<br />");  
});  
  
document.write("<br />");  
document.write(m.get(2));  
  
// Output:  
// black  
// red  
// 2  
// 3  
//  
// red  
  
```  
  
## Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]