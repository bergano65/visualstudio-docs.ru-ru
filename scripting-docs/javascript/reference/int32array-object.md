---
title: "Объект Int32Array | Microsoft Docs"
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
ms.assetid: 48696299-e41e-4590-b1b5-26fe19f68139
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Объект Int32Array
Типизированный массив 32\-разрядных целых значений.  Содержимое инициализируется значением 0.  Если запрошенное число байтов не удалось выделить, возникает исключение.  
  
## Синтаксис  
  
```  
  
      int32Array = new Int32Array( length );  
int32Array = new Int32Array( array );  
int32Array = new Int32Array( buffer, byteOffset, length);  
```  
  
## Параметры  
 `int32Array`  
 Обязательный.  Имя переменной, которой присваивается объект **Int32Array**.  
  
 `length`  
 Определяет количество элементов в массиве.  
  
 `array`  
 Массив \(или типизированный массив\), который содержится в этом массиве.  Содержимое инициализируется содержимым заданного массива или типизированного массива, при этом каждый элемент преобразуется в тип Int32.  
  
 `buffer`  
 Буфер ArrayBuffer, представляемый этим объектом Int32Array.  
  
 `byteOffset`  
 Необязательный.  Задает смещение в байтах от начала буфера, по которому должно начинаться представление Int32Array.  
  
 `length`  
 Количество элементов в массиве.  
  
## Константы  
 В следующей таблице перечислены константы объекта `Int32Array`.  
  
|Константа|Описание|  
|---------------|--------------|  
|[Константа BYTES\_PER\_ELEMENT](../../javascript/reference/bytes-per-element-constant-int32array.md)|Размер в байтах каждого элемента массива.|  
  
## Свойства  
 В следующей таблице перечислены константы объекта `Int32Array`.  
  
|Свойство|Описание|  
|--------------|--------------|  
|[Свойство buffer](../../javascript/reference/buffer-property-int32array.md)|Только для чтения.  Получает буфер ArrayBuffer, на который ссылается данный массив.|  
|[Свойство byteLength](../../javascript/reference/bytelength-property-int32array.md)|Только для чтения.  Длина данного массива от начала его буфера ArrayBuffer в байтах, зафиксированная во время создания.|  
|[Свойство byteOffset](../../javascript/reference/byteoffset-property-int32array.md)|Только для чтения.  Смещение данного массива от начала его буфера ArrayBuffer в байтах, зафиксированное во время создания.|  
|[Свойство length](../../javascript/reference/length-property-int32array.md)|Длина массива.|  
  
## Методы  
 В следующей таблице перечислены методы объекта `Int32Array`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[Метод set \(Int32Array\)](../../javascript/reference/set-method-int32array.md)|Задает значение или массив значений.|  
|[Метод subarray \(Int32Array\)](../../javascript/reference/subarray-method-int32array.md)|Получает новое представление Int32Array хранилища ArrayBuffer для данного массива.|  
  
## Пример  
 В следующем примере показано, как использовать объект Int32Array для обработки двоичных данных, полученных из запроса XMLHttpRequest:  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Int32Array(buffer.byteLength / 4);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getInt32(i * 4);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## Требования  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]