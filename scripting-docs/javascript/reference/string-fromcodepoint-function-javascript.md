---
title: "Функция String.fromCodePoint (JavaScript) | Microsoft Docs"
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
ms.assetid: 7c4c057b-c67a-4b10-afdd-4f75c7c5988c
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Функция String.fromCodePoint (JavaScript)
Возвращает строку, связанную с кодовой точкой Юникода UTF\-16.  
  
## Синтаксис  
  
```  
String.fromCodePoint(...codePoints);  
```  
  
#### Параметры  
 `…codePoints`  
 Обязательный.  Параметр  "остальное", который указывает одно значение или несколько значений кодовых точек UTF\-16.  
  
## Заметки  
 Эта функция вызывает исключение `RangeError`, если `...codePoints` не является допустимой кодовой точкой UTF\-16.  
  
## Пример  
 В следующем примере показано, как использовать функцию `fromCodePoint`.  
  
```javascript  
var str1 = String.fromCodePoint(0x20BB7);  
var str2 = String.fromCodePoint(98);  
var str3 = String.fromCodePoint(97, 98, 99);  
  
if(console && console.log) {  
    console.log(str1);  
    console.log(str2);  
    console.log(str3);  
}  
  
// Output:  
// 𠮷  
// b  
// abc  
  
```  
  
## Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]