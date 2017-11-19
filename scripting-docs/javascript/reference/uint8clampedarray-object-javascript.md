---
title: "Объект Uint8ClampedArray (JavaScript) | Документы Microsoft"
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
ms.assetid: 0c5537f7-00b4-487a-8fba-ef032e67e7bd
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 51673eadc8eb905355bf136dc82b2f240462180a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="uint8clampedarray-object-javascript"></a>Объект Uint8ClampedArray (JavaScript)
Типизированный массив 8-разрядных целых беззнаковых чисел со значениями, ограниченными диапазоном 0–255. Содержимое инициализируется значением 0. Если не удается выделить запрошенное число байт, возникает исключение.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
      uint8ClampedArray = new Uint8ClampedArray( length );  
uint8ClampedArray = new Uint8ClampedArray( array );  
uint8ClampedArray = new Uint8ClampedArray( buffer, byteOffset, length);  
```  
  
## <a name="parameters"></a>Параметры  
 `uint8ClampedArray`  
 Обязательный. Имя переменной, которой присваивается объект `Uint8ClampedArray`.  
  
 `length`  
 Необязательный. Количество элементов в массиве.  
  
 `array`  
 Необязательный. Массив (или типизированный массив), содержащийся в данном массиве. Содержимое инициализируется содержимым заданного массива или типизированного массива, при этом каждый элемент преобразуется в тип `Uint8`.  
  
 `buffer`  
 Необязательно. [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) , `Uint8ClampedArray` представляет.  
  
 `byteOffset`  
 Необязательно. Смещение в байтах от начала буфера, по которому должно начинаться представление `Uint8ClampedArray`.  
  
 `length`  
 Необязательный. Количество элементов в массиве.  
  
## <a name="remarks"></a>Примечания  
 Значения, хранимые в объекте `Uint8ClampedArray`, находятся в диапазоне 0–255. Если задать для члена массива отрицательное значение, в качестве значения задается 0. Если задать значение больше 255, в качестве значения задается 255.  
  
 Значения в `Uint8ClampedArray` объекта округляются до ближайшего четное значение, которое называется банковским округлением.  
  
## <a name="constants"></a>Константы  
 В следующей таблице перечислены константы объекта `Uint8ClampedArray`.  
  
|Константа|Описание|  
|--------------|-----------------|  
|[Константа BYTES_PER_ELEMENT](../../javascript/reference/bytes-per-element-constant-uint8clampedarray.md)|Размер в байтах каждого элемента массива.|  
  
## <a name="properties"></a>Свойства  
 В следующей таблице перечислены константы объекта `Uint8ClampedArray`.  
  
|Свойство|Описание|  
|--------------|-----------------|  
|[Свойство buffer](../../javascript/reference/buffer-property-uint8clampedarray.md)|Только для чтения. Возвращает [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) , на который ссылается этот массив.|  
|[Свойство byteLength](../../javascript/reference/bytelength-property-uint8clampedarray.md)|Только для чтения. Длина данного массива от начала его [ArrayBuffer](../../javascript/reference/arraybuffer-object.md), в байтах, зафиксированная во время создания.|  
|[Свойство byteOffset](../../javascript/reference/byteoffset-property-uint8clampedarray.md)|Только для чтения. Смещение данного массива от начала его [ArrayBuffer](../../javascript/reference/arraybuffer-object.md), в байтах, зафиксированная во время создания.|  
|[Свойство Length](../../javascript/reference/length-property-uint8clampedarray.md)|Длина массива.|  
  
## <a name="methods"></a>Методы  
 В следующей таблице перечислены методы объекта `Uint8ClampedArray`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[Метод Set](../../javascript/reference/set-method-uint8clampedarray.md)|Задает значение или массив значений.|  
|[Метод SubArray](../../javascript/reference/subarray-method-uint8clampedarray.md)|Получает новый `Uint8ClampedArray` представление [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) хранения для этого массива, указывая первый и последний элемент подмассива.|  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как использовать объект `Uint8ClampedArray` для обработки двоичных данных, полученных из запроса `XmlHttpRequest`:  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Uint8ClampedArray(buffer.byteLength);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getUint8(i);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## <a name="example"></a>Пример  
 Пример ниже демонстрирует ограничение значений в представлении `Uint8ClampedArray`.  
  
```JavaScript  
var ints = new Uint8ClampedArray(2);  
ints[0] = -1;  // 0 will be assigned.  
ints[1] = 256; // 255 will be assigned.  
  
```  
  
## <a name="example"></a>Пример  
 Пример ниже демонстрирует округление значений в представлении `Uint8ClampedArray`.  
  
```  
var ints = new Uint8ClampedArray(4);  
ints[0] = 11.3; // 11 will be assigned (same as Int8Array).  
ints[1] = 11.8; // 12 will be assigned (same as Int8Array).  
ints[2] = 10.5; // 10 will be assigned (rounded to the nearest   
                // even value).  
ints[3] = 11.5; // 12 will be assigned (rounded to the nearest   
                // even value).  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Объект Uint8Array](../../javascript/reference/uint8array-object.md)   
 [Объект ArrayBuffer](../../javascript/reference/arraybuffer-object.md)
