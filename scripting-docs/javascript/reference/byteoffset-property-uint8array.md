---
title: "Свойство byteOffset (Uint8Array) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 71dca368-6319-4175-a377-2b0b586ef78d
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fd77a2f092ade4ec5474537e3ffe27207d1200a1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="byteoffset-property-uint8array"></a>Свойство byteOffset (Uint8Array)
Только для чтения. Смещение данного массива от начала его буфера ArrayBuffer в байтах, зафиксированное во время создания.  
  
## <a name="syntax"></a>Синтаксис  
  
```JavaScript  
var arrayOffset = uint8Array.byteOffset;  
```  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как получить смещение массива.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var intArr = new Uint8Array(buffer.byteLength);  
            alert(intArr.byteOffset);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]