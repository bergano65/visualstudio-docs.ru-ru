---
title: "Объект Uint32Array | Документы Microsoft"
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
ms.assetid: c4bf5409-2d4b-4660-9f4b-a45d7a02b47e
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 05f185e02ac117491d067ddca6605197d126620e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="uint32array-object"></a>Объект Uint32Array
Типизированный массив 32-разрядных целых значений. Содержимое инициализируется значением 0. Если запрошенное число байтов не удалось выделить, возникает исключение.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
      uint32Array = new Uint32Array( length );  
uint32Array = new Uint32Array( array );  
uint32Array = new Uint32Array( buffer, byteOffset, length);  
```  
  
## <a name="parameters"></a>Параметры  
 `uint32Array`  
 Обязательный. Имя переменной, которой **Uint32Array** присваивается объект.  
  
 `length`  
 Определяет количество элементов в массиве.  
  
 `array`  
 Массив (или типизированный массив), который содержится в этом массиве. Содержимое инициализируется содержимым заданного массива или типизированного массива, при этом каждый элемент преобразуется в тип Uint32.  
  
 `buffer`  
 Буфер ArrayBuffer, представляемый этим объектом Uint32Array.  
  
 `byteOffset`  
 Необязательно. Задает смещение в байтах от начала буфера, по которому должно начинаться представление Uint32Array.  
  
 `length`  
 Количество элементов в массиве.  
  
## <a name="constants"></a>Константы  
 В следующей таблице перечислены константы объекта `Uint32Array`.  
  
|Константа|Описание|  
|--------------|-----------------|  
|[Константа BYTES_PER_ELEMENT](../../javascript/reference/bytes-per-element-constant-uint32array.md)|Размер в байтах каждого элемента массива.|  
  
## <a name="properties"></a>Свойства  
 В следующей таблице перечислены константы объекта `Uint32Array`.  
  
|Свойство|Описание|  
|--------------|-----------------|  
|[Свойство buffer](../../javascript/reference/buffer-property-uint32array.md)|Только для чтения. Получает буфер ArrayBuffer, на который ссылается данный массив.|  
|[Свойство byteLength](../../javascript/reference/bytelength-property-uint32array.md)|Только для чтения. Длина данного массива от начала его буфера ArrayBuffer в байтах, зафиксированная во время создания.|  
|[Свойство byteOffset](../../javascript/reference/byteoffset-property-uint32array.md)|Только для чтения. Смещение данного массива от начала его буфера ArrayBuffer в байтах, зафиксированное во время создания.|  
|[Свойство Length](../../javascript/reference/length-property-uint32array.md)|Длина массива.|  
  
## <a name="methods"></a>Методы  
 В следующей таблице перечислены методы объекта `Uint32Array`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[Метод set (Uint32Array)](../../javascript/reference/set-method-uint32array.md)|Задает значение или массив значений.|  
|[Метод subarray (Uint32Array)](../../javascript/reference/subarray-method-uint32array.md)|Получает новое представление Uint32Array хранилища ArrayBuffer для данного массива.|  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как использовать объект Uint32Array для обработки двоичных данных, полученных из запроса XMLHttpRequest:  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Uint32Array(buffer.byteLength / 4);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getUint32(i * 4);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]