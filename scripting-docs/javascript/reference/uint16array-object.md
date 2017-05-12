---
title: "Объект Uint16Array | Microsoft Docs"
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
ms.assetid: e684647d-04d0-41a9-9089-16612e18ec7d
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Объект Uint16Array
Типизированный массив 16\-разрядных целых значений без знака.  Содержимое инициализируется значением 0.  Если запрошенное число байтов не удалось выделить, возникает исключение.  
  
## Синтаксис  
  
```  
  
      uint16Array = new Uint16Array( length );  
uint16Array = new Uint16Array( array );  
uint16Array = new Uint16Array( buffer, byteOffset, length );  
```  
  
## Параметры  
 `uint16Array`  
 Обязательный.  Имя переменной, которой присваивается объект **Uint16Array**.  
  
 `length`  
 Определяет количество элементов в массиве.  
  
 `array`  
 Массив \(или типизированный массив\), который содержится в этом массиве.  Содержимое инициализируется содержимым заданного массива или типизированного массива, при этом каждый элемент преобразуется в тип Uint16.  
  
 `buffer`  
 Буфер ArrayBuffer, представляемый этим объектом Uint16Array.  
  
 `byteOffset`  
 Необязательный.  Задает смещение в байтах от начала буфера, по которому должно начинаться представление Uint16Array.  
  
 `length`  
 Количество элементов в массиве.  
  
## Константы  
 В следующей таблице перечислены константы объекта `Uint16Array`.  
  
|Константа|Описание|  
|---------------|--------------|  
|[Константа BYTES\_PER\_ELEMENT](../../javascript/reference/bytes-per-element-constant-uint16array.md)|Размер в байтах каждого элемента массива.|  
  
## Свойства  
 В следующей таблице перечислены константы объекта `Uint16Array`.  
  
|Свойство|Описание|  
|--------------|--------------|  
|[Свойство buffer](../../javascript/reference/buffer-property-uint16array.md)|Только для чтения.  Получает буфер ArrayBuffer, на который ссылается данный массив.|  
|[Свойство byteLength](../../javascript/reference/bytelength-property-uint16array.md)|Только для чтения.  Длина данного массива от начала его буфера ArrayBuffer в байтах, зафиксированная во время создания.|  
|[Свойство byteOffset](../../javascript/reference/byteoffset-property-uint16array.md)|Только для чтения.  Смещение данного массива от начала его буфера ArrayBuffer в байтах, зафиксированное во время создания.|  
|[Свойство length](../../javascript/reference/length-property-uint16array.md)|Длина массива.|  
|||  
  
## Методы  
 В следующей таблице перечислены методы объекта `Uint16Array`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[Метод set \(Uint16Array\)](../../javascript/reference/set-method-uint16array.md)|Задает значение или массив значений.|  
|[Метод subarray \(Uint16Array\)](../../javascript/reference/subarray-method-uint16array.md)|Получает новое представление Uint16Array хранилища ArrayBuffer для данного массива.|  
  
## Пример  
 В следующем примере показано, как использовать объект Uint16Array для обработки двоичных данных, полученных из запроса XMLHttpRequest:  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Uint16Array(buffer.byteLength / 2);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getUint16(i * 2);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## Требования  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]