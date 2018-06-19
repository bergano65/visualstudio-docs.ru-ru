---
title: Объект Uint8Array | Документы Microsoft
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
ms.assetid: ae78b3ee-b660-4625-ac7b-d414a0842c87
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 72002af4ca92d1104a3c3c3bb2339e63856a80a6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641494"
---
# <a name="uint8array-object"></a>Объект Uint8Array
Типизированный массив 8-разрядных целых значений без знака. Содержимое инициализируется значением 0. Если запрошенное число байтов не удалось выделить, возникает исключение.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
      uint8Array = new Uint8Array( length );  
uint8Array = new Uint8Array( array );  
uint8Array = new Uint8Array( buffer, byteOffset, length);  
```  
  
## <a name="parameters"></a>Параметры  
 `uint8Array`  
 Обязательный. Имя переменной, которой **Uint8Array** присваивается объект.  
  
 `length`  
 Определяет количество элементов в массиве.  
  
 `array`  
 Массив (или типизированный массив), который содержится в этом массиве. Содержимое инициализируется содержимым заданного массива или типизированного массива, при этом каждый элемент преобразуется в тип Uint8.  
  
 `buffer`  
 Буфер ArrayBuffer, представляемый этим объектом Uint8Array.  
  
 `byteOffset`  
 Необязательно. Задает смещение в байтах от начала буфера, по которому должно начинаться представление Uint8Array.  
  
 `length`  
 Количество элементов в массиве.  
  
## <a name="constants"></a>Константы  
 В следующей таблице перечислены константы объекта `Uint8Array`.  
  
|Константа|Описание|  
|--------------|-----------------|  
|[Константа BYTES_PER_ELEMENT](../../javascript/reference/bytes-per-element-constant-uint8array.md)|Размер в байтах каждого элемента массива.|  
  
## <a name="properties"></a>Свойства  
 В следующей таблице перечислены константы объекта `Uint8Array`.  
  
|Свойство|Описание|  
|--------------|-----------------|  
|[Свойство buffer](../../javascript/reference/buffer-property-uint8array.md)|Только для чтения. Получает буфер ArrayBuffer, на который ссылается данный массив.|  
|[Свойство byteLength](../../javascript/reference/bytelength-property-uint8array.md)|Только для чтения. Длина данного массива от начала его буфера ArrayBuffer в байтах, зафиксированная во время создания.|  
|[Свойство byteOffset](../../javascript/reference/byteoffset-property-uint8array.md)|Только для чтения. Смещение данного массива от начала его буфера ArrayBuffer в байтах, зафиксированное во время создания.|  
|[Свойство Length](../../javascript/reference/length-property-uint8array.md)|Длина массива.|  
|||  
  
## <a name="methods"></a>Методы  
 В следующей таблице перечислены методы объекта `Uint8Array`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[Метод set (Uint8Array)](../../javascript/reference/set-method-uint8array.md)|Задает значение или массив значений.|  
|[Метод subarray (Uint8Array)](../../javascript/reference/subarray-method-uint8array.md)|Получает новое представление Uint8Array хранилища ArrayBuffer для данного массива.|  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как использовать объект Uint8Array для обработки двоичных данных, полученных из запроса XMLHttpRequest:  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Uint8Array(buffer.byteLength);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getUint8(i);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]