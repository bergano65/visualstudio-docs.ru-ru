---
title: "Метод has (WeakSet) (JavaScript) | Microsoft Docs"
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
ms.assetid: e24f0876-26bd-4007-b12a-360bb6fa0951
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Метод has (WeakSet) (JavaScript)
Возвращает `true`, если `WeakSet` содержит указанный элемент.  
  
## Синтаксис  
  
```javascript  
setObj.has(obj)  
```  
  
#### Параметры  
 `setObj`  
 Обязательный.  Объект `WeakSet`.  
  
 `obj`  
 Обязательный.  Элемент для проверки.  
  
## Значение свойства, возвращаемое значение  
 `true`, если набор содержит указанный элемент.  
  
## Пример  
 В следующем примере показано, как добавлять элементы в `WeakSet`, а затем проверять, содержит ли набор конкретный элемент.  
  
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