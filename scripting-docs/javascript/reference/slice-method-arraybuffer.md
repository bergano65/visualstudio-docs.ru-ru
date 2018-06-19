---
title: Метод slice (ArrayBuffer) | Документы Microsoft
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
ms.assetid: 2dcc51ff-f444-4d51-80ba-3bcd845ba0ae
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 25fc10a02b4a3422a6720ad91c8bba29906da0e5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640494"
---
# <a name="slice-method-arraybuffer"></a>Метод slice (ArrayBuffer)
Возвращает фрагмент [ArrayBuffer](../../javascript/reference/arraybuffer-object.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
arrayBufferObj.slice(start, [end])   
```  
  
## <a name="parameters"></a>Параметры  
 `arrayBufferObj`  
 Обязательный. [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) разделе будут скопированы из объекта.  
  
 `start`  
 Обязательный. Индекс байта начала копируемого фрагмента.  
  
 `end`  
 Необязательный. Индекс байта конца копируемого фрагмента.  
  
## <a name="remarks"></a>Примечания  
 `slice` Возвращает [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) , содержащий указанную часть `arrayBufferObj`.  
  
 Метод `slice` выполняет копирование сегмента до байта, указанного параметром `end`, но не включая его. Если `start` или `end` является отрицательным, указанный индекс обрабатывается `length`  +  `start` или `end`, соответственно, где `length` длина [ArrayBuffer](../../javascript/reference/arraybuffer-object.md). Если параметр `end` не задан, извлечение продолжается до конца объекта `arrayBufferObj`. Если `end` предшествует `start`, байты не копируются в новый [ArrayBuffer](../../javascript/reference/arraybuffer-object.md).  
  
## <a name="example"></a>Пример  
 В следующем примере демонстрируется использование метода `slice`.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer1 = req.response;  
            var buffer2 = buffer1.slice(40, 48);  
            var dataview = new DataView(buffer2);  
            var ints = new Int32Array(buffer2.byteLength / 4);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getInt32(i * 4);  
            }  
        alert(ints[1]);  
        }  
    }  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Объект ArrayBuffer](../../javascript/reference/arraybuffer-object.md)