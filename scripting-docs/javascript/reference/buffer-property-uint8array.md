---
title: Свойство Buffer (Uint8Array) | Документы Microsoft
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
ms.assetid: bb10f4db-d9a0-4f94-9497-a8719c94a717
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 62227881f16ff528e57e4bbc6e8db5170bb84f92
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633604"
---
# <a name="buffer-property-uint8array"></a>Свойство buffer (Uint8Array)
Только для чтения. Получает буфер ArrayBuffer, на который ссылается данный массив.  
  
## <a name="syntax"></a>Синтаксис  
  
```JavaScript  
var arrayBuffer = uint8Array.buffer;  
```  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как получить буфер ArrayBuffer массива.  
  
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
            alert(intArr.buffer.byteLength);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]