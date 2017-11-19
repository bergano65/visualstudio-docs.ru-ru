---
title: "Свойство byteLength (Float32Array) | Документы Microsoft"
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
ms.assetid: ea55beb2-e79f-4706-bcc9-6fdbf89e0fe9
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1c4b403a6632b143961df541dc13b03c9208d274
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="bytelength-property-float32array"></a>Свойство byteLength (Float32Array)
Только для чтения. Длина данного массива от начала его буфера ArrayBuffer в байтах, зафиксированная во время создания.  
  
## <a name="syntax"></a>Синтаксис  
  
```JavaScript  
var arrayByteLength = float32Array.byteLength;  
```  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как получить длину массива.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var floatArr = new Float32Array(buffer.byteLength) / 4);  
            alert(floatArr.byteLength);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]