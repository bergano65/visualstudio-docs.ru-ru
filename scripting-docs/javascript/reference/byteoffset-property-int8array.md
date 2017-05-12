---
title: "Свойство byteOffset (Int8Array) | Microsoft Docs"
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
ms.assetid: b155bf97-d567-4921-8edd-dbca0d84b6cf
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Свойство byteOffset (Int8Array)
Только для чтения.  Смещение данного массива от начала его ArrayBuffer в байтах, зафиксированное во время создания.  
  
## Синтаксис  
  
```javascript  
var arrayOffset = int8Array.byteOffset;  
```  
  
## Пример  
 В следующем примере показано, как получить смещение массива.  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var intArr = new Int8Array(buffer.byteLength);  
            alert(intArr.byteOffset);  
        }  
    }  
  
```  
  
## Требования  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]