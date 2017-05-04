---
title: "Функция Array.from (Array) (JavaScript) | Microsoft Docs"
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
ms.assetid: 1bf59a99-f860-4c4d-b4c6-d5f1f946a490
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Функция Array.from (Array) (JavaScript)
Возвращает массив из итерируемого объекта или объекта, имеющего вид массива.  
  
## Синтаксис  
  
```  
Array.from (arrayLike [ , mapfn [ , thisArg ] ] );  
```  
  
#### Параметры  
 `arrayLike`  
 Обязательный.  Итерируемый объект или объект, имеющий вид массива.  
  
 `mapfn`  
 Необязательный.  Функция сопоставления, которую необходимо вызвать для каждого элемента в `arrayLike`.  
  
 `thisArg`  
 Необязательный.  Определяет объект `this` в функции сопоставления.  
  
## Заметки  
 Параметр `arrayLike` должен быть либо объектом с индексированными элементами и свойством `length`, либо итерируемым объектом, таким как объект `Set`.  
  
 Необязательная функция сопоставления вызывается для каждого элемента в массиве.  
  
## Пример  
 В следующем примере возвращается массив из коллекции узлов элементов DOM.  
  
```javascript  
var elemArr = Array.from(document.querySelectorAll('*'));  
var elem = elemArr[0]; // elem contains a reference to the first DOM element  
  
```  
  
## Пример  
 В следующем примере возвращается массив символов.  
  
```javascript  
var charArr = Array.from("abc");  
// charArr[0] == "a";  
```  
  
## Пример  
 В следующем примере возвращается массив объектов, содержащихся в коллекции.  
  
```javascript  
var setObj = new Set("a", "b", "c");  
var objArr = Array.from(setObj);  
// objArr[1] == "b";  
  
```  
  
## Пример  
 В следующем примере показано, как изменять значение элементов, используя синтаксис стрелок и функцию сопоставления.  
  
```javascript  
var arr = Array.from([1, 2, 3], x => x * 10);  
// arr[0] == 10;  
// arr[1] == 20;  
// arr[2] == 30;  
```  
  
## Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]