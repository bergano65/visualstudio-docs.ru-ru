---
title: Объект Float64Array | Документы Microsoft
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
ms.assetid: 74c945dc-56ae-458c-b0aa-782f240e9b6c
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20544812d94c1234d85d714f6e469d0de4f4c5ab
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637414"
---
# <a name="float64array-object"></a>Объект Float64Array
Типизированный массив 64-разрядных значений с плавающей запятой. Содержимое инициализируется значением 0. Если запрошенное число байтов не удалось выделить, возникает исключение.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
      float64Array = new Float64Array( length );  
float64Array = new Float64Array( array );  
float64Array = new Float64Array( buffer, byteOffset, length);  
```  
  
## <a name="parameters"></a>Параметры  
 `float64Array`  
 Обязательный. Имя переменной, которой **Float64Array** присваивается объект.  
  
 `length`  
 Определяет количество элементов в массиве.  
  
 `array`  
 Массив (или типизированный массив), который содержится в этом массиве. Содержимое инициализируется содержимым заданного массива или типизированного массива, при этом каждый элемент преобразуется в тип Float64.  
  
 `buffer`  
 Буфер ArrayBuffer, представляемый этим объектом Float64Array.  
  
 `byteOffset`  
 Необязательный. Задает смещение в байтах от начала буфера, по которому должно начинаться представление Float64Array.  
  
 `length`  
 Количество элементов в массиве.  
  
## <a name="constants"></a>Константы  
 В следующей таблице перечислены константы объекта `Float64Array`.  
  
|Константа|Описание|  
|--------------|-----------------|  
|[Константа BYTES_PER_ELEMENT](../../javascript/reference/bytes-per-element-constant-float64array.md)|Размер в байтах каждого элемента массива.|  
  
## <a name="properties"></a>Свойства  
 В следующей таблице перечислены константы объекта `Float64Array`.  
  
|Свойство|Описание|  
|--------------|-----------------|  
|[Свойство buffer](../../javascript/reference/bytelength-property-float64array.md)|Только для чтения. Получает буфер ArrayBuffer, на который ссылается данный массив.|  
|[Свойство byteLength](../../javascript/reference/bytelength-property-float64array.md)|Только для чтения. Длина данного массива от начала его буфера ArrayBuffer в байтах, зафиксированная во время создания.|  
|[Свойство byteOffset](../../javascript/reference/length-property-float64array.md)|Только для чтения. Смещение данного массива от начала его буфера ArrayBuffer в байтах, зафиксированное во время создания.|  
|[Свойство Length](../../javascript/reference/length-property-float64array.md)|Длина массива.|  
  
## <a name="methods"></a>Методы  
 В следующей таблице перечислены методы объекта `Float64Array`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[GET-метод](../../javascript/reference/get-method-float64array.md)|Может быть опущен. Получает элемент с указанным индексом.|  
|[Метод set (Float64Array)](../../javascript/reference/set-method-float64array.md)|Задает значение или массив значений.|  
|[Метод subarray (Float64Array)](../../javascript/reference/subarray-method-float64array.md)|Получает новое представление Float64Array хранилища ArrayBuffer для данного массива.|  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как использовать объект Float64Array для обработки двоичных данных, полученных из запроса XMLHttpRequest:  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Float64Array(buffer.byteLength / 8);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getFloat64(i * 8);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]