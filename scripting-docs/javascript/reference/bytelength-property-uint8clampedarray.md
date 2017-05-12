---
title: "Свойство byteLength (Uint8ClampedArray) | Microsoft Docs"
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
ms.assetid: 37ae1728-8e2c-496c-bb77-f5f85b1ecbba
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Свойство byteLength (Uint8ClampedArray)
Только для чтения.  Длина данного массива от начала его буфера [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) в байтах, зафиксированная во время создания.  
  
## Синтаксис  
  
```javascript  
var arrayByteLength = uint8ClampedArray.byteLength;  
```  
  
## Пример  
 В следующем примере показано, как получить длину массива.  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var intArr = new Uint8ClampedArray(buffer.byteLength);  
            alert(intArr.byteLength);  
        }  
    }  
  
```  
  
## Требования  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## См. также  
 [Объект ArrayBuffer](../../javascript/reference/arraybuffer-object.md)   
 [Объект Uint8ClampedArray](../../javascript/reference/uint8clampedarray-object-javascript.md)