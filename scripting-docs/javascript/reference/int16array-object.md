---
title: Объект Int16Array | Документы Microsoft
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
ms.assetid: b87f36b4-4e38-4f32-b258-654c4ad2c615
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 550208f0f13ac05f96c13b240952d59ee62c097e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637824"
---
# <a name="int16array-object"></a>Объект Int16Array
Типизированный массив 16-разрядных целых значений. Содержимое инициализируется значением 0. Если запрошенное число байтов не удалось выделить, возникает исключение.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
      int16Array = new Int16Array( length );  
int16Array = new Int16Array( array );  
int16Array = new Int16Array( buffer, byteOffset, length);  
```  
  
## <a name="parameters"></a>Параметры  
 `int16Array`  
 Обязательный. Имя переменной, которой **Int16Array** присваивается объект.  
  
 `length`  
 Определяет количество элементов в массиве.  
  
 `array`  
 Массив (или типизированный массив), который содержится в этом массиве. Содержимое инициализируется содержимым заданного массива или типизированного массива, при этом каждый элемент преобразуется в тип Int16.  
  
 `buffer`  
 Буфер ArrayBuffer, представляемый этим объектом Int16Array.  
  
 `byteOffset`  
 Необязательно. Задает смещение в байтах от начала буфера, по которому должно начинаться представление Int16Array.  
  
 `length`  
 Количество элементов в массиве.  
  
## <a name="constants"></a>Константы  
 В следующей таблице перечислены константы объекта `Int16Array`.  
  
|Константа|Описание|  
|--------------|-----------------|  
|[Константа BYTES_PER_ELEMENT](../../javascript/reference/bytes-per-element-constant-int16array.md)|Размер в байтах каждого элемента массива.|  
  
## <a name="properties"></a>Свойства  
 В следующей таблице перечислены константы объекта `Int16Array`.  
  
|Свойство|Описание|  
|--------------|-----------------|  
|[Свойство buffer](../../javascript/reference/buffer-property-int16array.md)|Только для чтения. Получает буфер ArrayBuffer, на который ссылается данный массив.|  
|[Свойство byteLength](../../javascript/reference/byteoffset-property-int16array.md)|Только для чтения. Длина данного массива от начала его буфера ArrayBuffer в байтах, зафиксированная во время создания.|  
|[Свойство byteOffset](../../javascript/reference/byteoffset-property-int16array.md)|Только для чтения. Смещение данного массива от начала его буфера ArrayBuffer в байтах, зафиксированное во время создания.|  
|[Свойство Length](../../javascript/reference/length-property-int16array.md)|Длина массива.|  
  
## <a name="methods"></a>Методы  
 В следующей таблице перечислены методы объекта `Int16Array`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[Метод set (Int16Array)](../../javascript/reference/set-method-int16array.md)|Задает значение или массив значений.|  
|[Метод subarray (Int16Array)](../../javascript/reference/subarray-method-int16array.md)|Получает новое представление Int16Array хранилища ArrayBuffer для данного массива.|  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как использовать объект Int16Array для обработки двоичных данных, полученных из запроса XMLHttpRequest:  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Int16Array(buffer.byteLength / 2);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getInt16(i * 2);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]