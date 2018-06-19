---
title: Свойство byteOffset (Uint8ClampedArray) | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: bfc22cf4-00e3-4e2c-8419-032b179aa8da
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7997c90f59796f519cdeb4cab3f88965539d460b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633694"
---
# <a name="byteoffset-property-uint8clampedarray"></a>Свойство byteOffset (Uint8ClampedArray)
Только для чтения. Смещение данного массива от начала его [ArrayBuffer](../../javascript/reference/arraybuffer-object.md), в байтах, зафиксированная во время создания.  
  
## <a name="syntax"></a>Синтаксис  
  
```JavaScript  
var arrayOffset = uint8ClampedArray.byteOffset;  
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
            var intArr = new Uint8ClampedArray(buffer.byteLength);  
            alert(intArr.byteOffset);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Объект ArrayBuffer](../../javascript/reference/arraybuffer-object.md)   
 [Объект Uint8ClampedArray](../../javascript/reference/uint8clampedarray-object-javascript.md)