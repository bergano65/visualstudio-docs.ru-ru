---
title: "Объект Float32Array | Microsoft Docs"
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
ms.assetid: 4b29456a-1488-4006-ae66-5bf4c05003b1
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Объект Float32Array
Типизированный массив 32\-разрядных значений с плавающей запятой.  Содержимое инициализируется значением 0.  Если запрошенное число байтов не удалось выделить, возникает исключение.  
  
## Синтаксис  
  
```  
  
float32Array = new Float32Array( length ); float32Array = new Float32Array( array ); float32Array = new Float32Array( buffer, byteOffset, length);  
```  
  
## Параметры  
 `float32Array`  
 Обязательный.  Имя переменной, которой присваивается объект **Float32Array**.  
  
 `length`  
 Определяет количество элементов в массиве.  
  
 `array`  
 Массив \(или типизированный массив\), который содержится в этом массиве.  Содержимое инициализируется содержимым заданного массива или типизированного массива, при этом каждый элемент преобразуется в тип Float32.  
  
 `buffer`  
 Буфер ArrayBuffer, представляемый этим объектом Float32Array.  
  
 `byteOffset`  
 Необязательный.  Задает смещение в байтах от начала буфера, по которому должно начинаться представление Float32Array.  
  
 `length`  
 Количество элементов в массиве.  
  
## Константы  
 В следующей таблице перечислены константы объекта `Float32Array`.  
  
|Константа|Описание|  
|---------------|--------------|  
|[Константа BYTES\_PER\_ELEMENT](../../javascript/reference/bytes-per-element-constant-float32array.md)|Размер в байтах каждого элемента массива.|  
  
## Свойства  
 В следующей таблице перечислены константы объекта `Float32Array`.  
  
|Свойство|Описание|  
|--------------|--------------|  
|[Свойство buffer](../../javascript/reference/buffer-property-float32array.md)|Только для чтения.  Получает буфер ArrayBuffer, на который ссылается данный массив.|  
|[Свойство byteLength](../../javascript/reference/bytelength-property-float32array.md)|Только для чтения.  Длина данного массива от начала его буфера ArrayBuffer в байтах, зафиксированная во время создания.|  
|[Свойство byteOffset](../../javascript/reference/byteoffset-property-float32array.md)|Только для чтения.  Смещение данного массива от начала его буфера ArrayBuffer в байтах, зафиксированное во время создания.|  
|[Свойство length](../../javascript/reference/length-property-float32array.md)|Длина массива.|  
|||  
  
## Методы  
 В следующей таблице перечислены методы объекта `Float32Array`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[Метод get](../../javascript/reference/get-method-float32array.md)|Может быть опущен.  Получает элемент с указанным индексом.|  
|[Метод set \(Float32Array\)](../../javascript/reference/set-method-float32array.md)|Задает значение или массив значений.|  
|[Метод subarray \(Float32Array\)](../../javascript/reference/subarray-method-float32array.md)|Получает новое представление Float32Array хранилища ArrayBuffer для данного массива.|  
  
## Пример  
 В следующем примере показано, как использовать объект Float32Array для обработки двоичных данных, полученных из запроса XMLHttpRequest:  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Float32Array(buffer.byteLength / 4);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getFloat32(i * 4);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## Требования  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]