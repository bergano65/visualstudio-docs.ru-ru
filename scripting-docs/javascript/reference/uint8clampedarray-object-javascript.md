---
title: "Объект Uint8ClampedArray (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 0c5537f7-00b4-487a-8fba-ef032e67e7bd
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Объект Uint8ClampedArray (JavaScript)
Типизированный массив 8\-разрядных целых беззнаковых чисел со значениями, ограниченными диапазоном 0–255.  Содержимое инициализируется значением 0.  Если не удается выделить запрошенное число байт, возникает исключение.  
  
## Синтаксис  
  
```  
  
uint8ClampedArray = new Uint8ClampedArray( length ); uint8ClampedArray = new Uint8ClampedArray( array ); uint8ClampedArray = new Uint8ClampedArray( buffer, byteOffset, length);  
```  
  
## Параметры  
 `uint8ClampedArray`  
 Обязательный.  Имя переменной, которой присваивается объект `Uint8ClampedArray`.  
  
 `length`  
 Необязательный.  Количество элементов в массиве.  
  
 `array`  
 Необязательный.  Массив \(или типизированный массив\), содержащийся в данном массиве.  Содержимое инициализируется содержимым заданного массива или типизированного массива, при этом каждый элемент преобразуется в тип `Uint8`.  
  
 `buffer`  
 Необязательный.  Буфер [ArrayBuffer](../../javascript/reference/arraybuffer-object.md), представляемый этим объектом `Uint8ClampedArray`.  
  
 `byteOffset`  
 Необязательный.  Смещение в байтах от начала буфера, по которому должно начинаться представление `Uint8ClampedArray`.  
  
 `length`  
 Необязательный.  Количество элементов в массиве.  
  
## Заметки  
 Значения, хранимые в объекте `Uint8ClampedArray`, находятся в диапазоне 0–255.  Если задать для члена массива отрицательное значение, в качестве значения задается 0.  Если задать значение больше 255, в качестве значения задается 255.  
  
 Значения в объекте `Uint8ClampedArray` округляются до ближайшего четного значения \(такой способ называется банковским округлением\).  
  
## Константы  
 В следующей таблице перечислены константы объекта `Uint8ClampedArray`.  
  
|Константа|Описание|  
|---------------|--------------|  
|[Константа BYTES\_PER\_ELEMENT](../../javascript/reference/bytes-per-element-constant-uint8clampedarray.md)|Размер в байтах каждого элемента массива.|  
  
## Свойства  
 В следующей таблице перечислены константы объекта `Uint8ClampedArray`.  
  
|Свойство|Описание|  
|--------------|--------------|  
|[Свойство buffer](../../javascript/reference/buffer-property-uint8clampedarray.md)|Только для чтения.  Получает буфер [ArrayBuffer](../../javascript/reference/arraybuffer-object.md), на который ссылается данный массив.|  
|[Свойство byteLength](../../javascript/reference/bytelength-property-uint8clampedarray.md)|Только для чтения.  Длина данного массива от начала его буфера [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) в байтах, зафиксированная во время создания.|  
|[Свойство byteOffset](../../javascript/reference/byteoffset-property-uint8clampedarray.md)|Только для чтения.  Смещение данного массива от начала его буфера [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) в байтах, зафиксированное во время создания.|  
|[Свойство length](../../javascript/reference/length-property-uint8clampedarray.md)|Длина массива.|  
  
## Методы  
 В следующей таблице перечислены методы объекта `Uint8ClampedArray`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[Метод set](../../javascript/reference/set-method-uint8clampedarray.md)|Задает значение или массив значений.|  
|[Метод subarray](../../javascript/reference/subarray-method-uint8clampedarray.md)|Получает новое представление `Uint8ClampedArray` хранилища [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) для этого массива, указывая первый и последний элемент подмассива.|  
  
## Пример  
 В следующем примере показано, как использовать объект `Uint8ClampedArray` для обработки двоичных данных, полученных из запроса `XmlHttpRequest`:  
  
```javascript  
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
  
## Пример  
 Пример ниже демонстрирует ограничение значений в представлении `Uint8ClampedArray`.  
  
```javascript  
var ints = new Uint8ClampedArray(2);  
ints[0] = -1;  // 0 will be assigned.  
ints[1] = 256; // 255 will be assigned.  
  
```  
  
## Пример  
 Пример ниже демонстрирует округление значений в представлении `Uint8ClampedArray`.  
  
```  
var ints = new Uint8ClampedArray(4);  
ints[0] = 11.3; // 11 will be assigned (same as Int8Array).  
ints[1] = 11.8; // 11 will be assigned (same as Int8Array).  
ints[2] = 10.5; // 10 will be assigned (rounded to the nearest   
                // even value).  
ints[3] = 11.5; // 12 will be assigned (rounded to the nearest   
                // even value).  
  
```  
  
## Требования  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## См. также  
 [Объект Uint8Array](../../javascript/reference/uint8array-object.md)   
 [Объект ArrayBuffer](../../javascript/reference/arraybuffer-object.md)