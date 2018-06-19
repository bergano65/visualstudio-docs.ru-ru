---
title: Объект Int8Array | Документы Microsoft
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
ms.assetid: 0e3bdbc5-8d85-4c0d-b399-693b01674803
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7e3f85a505f41f2909330e938f4978433fc823f9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637794"
---
# <a name="int8array-object"></a>Объект Int8Array
Типизированный массив 8-разрядных целых значений. Содержимое инициализируется значением 0. Если запрошенное число байтов не удалось выделить, возникает исключение.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
      int8Array = new Int8Array( length );  
intArray = new Int8Array( array );  
intArray = new Int8Array( buffer, byteOffset, length);  
```  
  
## <a name="parameters"></a>Параметры  
 `int8Array`  
 Обязательный. Имя переменной, которой присваивается объект `Int8Array`.  
  
 `length`  
 Определяет количество элементов в массиве.  
  
 `array`  
 Массив (или типизированный массив), который содержится в этом массиве. Содержимое инициализируется содержимым заданного массива или типизированного массива, при этом каждый элемент преобразуется в тип Int8.  
  
 `buffer`  
 Буфер ArrayBuffer, представляемый данным объектом Int8Array.  
  
 `byteOffset`  
 Необязательно. Задает смещение в байтах от начала буфера, по которому должно начинаться представление Int8Array.  
  
 `length`  
 Количество элементов в массиве.  
  
## <a name="constants"></a>Константы  
 В следующей таблице перечислены константы объекта `Int8Array`.  
  
|Константа|Описание|  
|--------------|-----------------|  
|[Константа BYTES_PER_ELEMENT](../../javascript/reference/bytes-per-element-constant-int8array.md)|Размер в байтах каждого элемента массива.|  
  
## <a name="properties"></a>Свойства  
 В следующей таблице перечислены константы объекта `Int8Array`.  
  
|Свойство|Описание|  
|--------------|-----------------|  
|[Свойство buffer](../../javascript/reference/buffer-property-int8array.md)|Только для чтения. Получает буфер ArrayBuffer, на который ссылается данный массив.|  
|[Свойство byteLength](../../javascript/reference/bytelength-property-int8array.md)|Только для чтения. Длина данного массива от начала его буфера ArrayBuffer в байтах, зафиксированная во время создания.|  
|[Свойство byteOffset](../../javascript/reference/byteoffset-property-int8array.md)|Только для чтения. Смещение данного массива от начала его буфера ArrayBuffer в байтах, зафиксированное во время создания.|  
|[Свойство Length](../../javascript/reference/length-property-int8array.md)|Длина массива.|  
  
## <a name="methods"></a>Методы  
 В следующей таблице перечислены методы объекта `Int8Array`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[Метод set (Int8Array)](../../javascript/reference/set-method-int8array.md)|Задает значение или массив значений.|  
|[Метод subarray (Int8Array)](../../javascript/reference/subarray-method-int8array.md)|Получает новое представление Int8Array хранилища ArrayBuffer для данного массива.|  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как использовать объект Int8Array для обработки двоичных данных, полученных из запроса XMLHttpRequest:  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Int8Array(buffer.byteLength);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getInt8(i);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]