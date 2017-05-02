---
title: "Метод add (WeakSet) (JavaScript) | Microsoft Docs"
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
ms.assetid: d35d0287-6b33-4720-b9d7-8954c428ce4e
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Метод add (WeakSet) (JavaScript)
Добавляет новый элемент в `WeakSet`.  
  
## Синтаксис  
  
```javascript  
weaksetObj.add(obj)  
```  
  
#### Параметры  
 `weaksetObj`  
 Обязательный.  Объект `WeakSet`.  
  
 `obj`  
 Обязательный.  Новый элемент набора `WeakSet`.  
  
## Заметки  
 Новый элемент должен быть объектом, а не произвольным значением и должен быть уникальным.  При добавлении неуникального элемента в набор `WeakSet` новый элемент не будет добавлен в коллекцию.  
  
## Пример  
 В следующем примере показано, как добавлять элементы в набор и проверять, что они были добавлены.  
  
```javascript  
var ws = new WeakSet();  
  
var str = new String("Thomas Jefferson");  
var num = new Number(1776);  
  
ws.add(str);  
ws.add(num);  
  
console.log(ws.has(str));  
console.log(ws.has(num));  
  
ws.delete(str);  
console.log(ws.has(str));  
  
// Output:  
// true  
// true  
// false  
  
```  
  
## Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]