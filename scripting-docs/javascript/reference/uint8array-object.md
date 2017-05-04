---
title: "Объект Uint8Array | Microsoft Docs"
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
ms.assetid: ae78b3ee-b660-4625-ac7b-d414a0842c87
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Объект Uint8Array
Типизированный массив 8\-разрядных целых значений без знака.  Содержимое инициализируется значением 0.  Если запрошенное число байтов не удалось выделить, возникает исключение.  
  
## Синтаксис  
  
```  
  
      uint8Array = new Uint8Array( length );  
uint8Array = new Uint8Array( array );  
uint8Array = new Uint8Array( buffer, byteOffset, length);  
```  
  
## Параметры  
 `uint8Array`  
 Обязательный.  Имя переменной, которой присваивается объект **Uint8Array**.  
  
 `length`  
 Определяет количество элементов в массиве.  
  
 `array`  
 Массив \(или типизированный массив\), который содержится в этом массиве.  Содержимое инициализируется содержимым заданного массива или типизированного массива, при этом каждый элемент преобразуется в тип Uint8.  
  
 `buffer`  
 Буфер ArrayBuffer, представляемый этим объектом Uint8Array.  
  
 `byteOffset`  
 Необязательный.  Задает смещение в байтах от начала буфера, по которому должно начинаться представление Uint8Array.  
  
 `length`  
 Количество элементов в массиве.  
  
## Константы  
 В следующей таблице перечислены константы объекта `Uint8Array`.  
  
|Константа|Описание|  
|---------------|--------------|  
|[Константа BYTES\_PER\_ELEMENT](../../javascript/reference/bytes-per-element-constant-uint8array.md)|Размер в байтах каждого элемента массива.|  
  
## Свойства  
 В следующей таблице перечислены константы объекта `Uint8Array`.  
  
|Свойство|Описание|  
|--------------|--------------|  
|[Свойство buffer](../../javascript/reference/buffer-property-uint8array.md)|Только для чтения.  Получает буфер ArrayBuffer, на который ссылается данный массив.|  
|[Свойство byteLength](../../javascript/reference/bytelength-property-uint8array.md)|Только для чтения.  Длина данного массива от начала его буфера ArrayBuffer в байтах, зафиксированная во время создания.|  
|[Свойство byteOffset](../../javascript/reference/byteoffset-property-uint8array.md)|Только для чтения.  Смещение данного массива от начала его буфера ArrayBuffer в байтах, зафиксированное во время создания.|  
|[Свойство length](../../javascript/reference/length-property-uint8array.md)|Длина массива.|  
|||  
  
## Методы  
 В следующей таблице перечислены методы объекта `Uint8Array`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[Метод set \(Uint8Array\)](../../javascript/reference/set-method-uint8array.md)|Задает значение или массив значений.|  
|[Метод subarray \(Uint8Array\)](../../javascript/reference/subarray-method-uint8array.md)|Получает новое представление Uint8Array хранилища ArrayBuffer для данного массива.|  
  
## Пример  
 В следующем примере показано, как использовать объект Uint8Array для обработки двоичных данных, полученных из запроса XMLHttpRequest:  
  
```javascript  
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
  
## Требования  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]