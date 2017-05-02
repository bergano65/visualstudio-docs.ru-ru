---
title: "Метод codePointAt (String) (JavaScript) | Microsoft Docs"
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
ms.assetid: 7979018f-1be3-4a13-9e8f-c84c7ed35288
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Метод codePointAt (String) (JavaScript)
Возвращает кодовую точку для символа Юникода UTF\-16.  
  
## Синтаксис  
  
```  
stringObj.codePointAt(pos);  
```  
  
#### Параметры  
 `stringObj`  
 Обязательный.  Строковый объект.  
  
 `pos`  
 Обязательный.  Позиция символа.  
  
## Заметки  
 Этот метод возвращает значения кодовых точек, включая астральные кодовые точки \(кодовые точки с более чем четырьмя шестнадцатеричными значениями\) для всех символов UTF\-16.  
  
 Если `pos` меньше нуля \(0\) или больше размера строки, возвращаемое значение — `undefined`.  
  
## Пример  
 В следующем примере показано, как использовать метод `codePointAt`.  
  
```javascript  
var cp1 = "𠮷".codePointAt(0);  
vary cp2 = 'abc'.codePointAt(1);  
  
if(console && console.log) {  
    console.log(cp1);  
    console.log(cp2);}  
  
// Output:  
// 0x20BB7  
// 98  
  
```  
  
## Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]