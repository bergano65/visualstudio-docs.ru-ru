---
title: "Объект DataView | Microsoft Docs"
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
ms.assetid: 250ec067-7505-4ee0-82ab-bfd3c2820afa
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Объект DataView
Объект DataView можно использовать для чтения и записи различных типов двоичных данных в любом месте в ArrayBuffer.  
  
## Синтаксис  
  
```  
  
dataView = new DataView(buffer, byteOffset, byteLength);  
```  
  
## Параметры  
 `dataView`  
 Обязательное.  Имя переменной, которой присваивается объект **DataView**.  
  
 `buffer`  
 ArrayBuffer, представляемый данным DataView.  
  
 `byteOffset`  
 Необязательный параметр.  Задает смещение в байтах от начала буфера, по которому должно начинаться представление DataView.  
  
 `byteLength`  
 Необязательный параметр.  Задает длину \(в байтах\) раздела буфера, который должно представлять DataView.  
  
## Заметки  
 Если и byteOffset, и byteLength опущены, DataView охватывает весь диапазон ArrayBuffer.  Если аргумент byteLength опущен, DataView охватывает диапазон от смещения, заданного аргументом byteOffset, до конца ArrayBuffer.  Если значения в аргументах byteOffset и byteLength ссылаются на область за пределами ArrayBuffer, вызывается исключение.  
  
## Свойства  
 В следующей таблице перечислены свойства объекта `DataView`.  
  
|Свойство|Описание|  
|--------------|--------------|  
|[Свойство buffer](../../javascript/reference/buffer-property-dataview.md)|Только для чтения.  Получает ArrayBuffer, на который ссылается данное представление.|  
|[Свойство byteLength](../../javascript/reference/bytelength-property-dataview.md)|Только для чтения.  Длина данного представления от начала его ArrayBuffer в байтах, зафиксированная во время создания.|  
|[Свойство byteOffset](../../javascript/reference/byteoffset-property-dataview.md)|Только для чтения.  Смещение данного представления от начала его ArrayBuffer в байтах, зафиксированное во время создания.|  
  
## Методы  
 В следующей таблице перечислены методы объекта `DataView`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[Метод getInt8](../../javascript/reference/getint8-method-dataview.md)|Получает значение Int8 по указанному смещению в байтах от начала представления.|  
|[Метод getUint8 \(DataView\)](../../javascript/reference/getuint8-method-dataview.md)|Получает значение Uint8 по указанному смещению в байтах от начала представления.|  
|[Метод getInt16 \(DataView\)](../../javascript/reference/getint16-method-dataview.md)|Получает значение Int16 по указанному смещению в байтах от начала представления.|  
|[Метод getUint16 \(DataView\)](../../javascript/reference/getuint16-method-dataview.md)|Получает значение Uint16 по указанному смещению в байтах от начала представления.|  
|[Метод getInt32 \(DataView\)](../../javascript/reference/getint32-method-dataview.md)|Получает значение Int32 по указанному смещению в байтах от начала представления.|  
|[Метод getUint32 \(DataView\)](../../javascript/reference/getuint32-method-dataview.md)|Получает значение Uint32 по указанному смещению в байтах от начала представления.|  
|[Метод getFloat32 \(DataView\)](../../javascript/reference/getfloat32-method-dataview.md)|Получает значение Float32 по указанному смещению в байтах от начала представления.|  
|[Метод getFloat64 \(DataView\)](../../javascript/reference/getfloat64-method-dataview.md)|Получает значение Float64 по указанному смещению в байтах от начала представления.|  
|[Метод setInt8 \(DataView\)](../../javascript/reference/setint8-method-dataview.md)|Сохраняет значение Int8 по указанному смещению в байтах от начала представления.|  
|[Метод setUint8 \(DataView\)](../../javascript/reference/setuint8-method-dataview.md)|Сохраняет значение Uint8 по указанному смещению в байтах от начала представления.|  
|[Метод setInt16 \(DataView\)](../../javascript/reference/setint16-method-dataview.md)|Сохраняет значение Int16 по указанному смещению в байтах от начала представления.|  
|[Метод setUint16 \(DataView\)](../../javascript/reference/setuint16-method-dataview.md)|Сохраняет значение Uint16 по указанному смещению в байтах от начала представления.|  
|[Метод setInt32 \(DataView\)](../../javascript/reference/setint32-method-dataview.md)|Сохраняет значение Int32 по указанному смещению в байтах от начала представления.|  
|[Метод setUint32 \(DataView\)](../../javascript/reference/setuint32-method-dataview.md)|Сохраняет значение Uint32 по указанному смещению в байтах от начала представления.|  
|[Метод setFloat32 \(DataView\)](../../javascript/reference/setfloat32-method-dataview.md)|Сохраняет значение Float32 по указанному смещению в байтах от начала представления.|  
|[Метод setFloat64 \(DataView\)](../../javascript/reference/setfloat64-method-dataview.md)|Сохраняет значение Float64 по указанному смещению в байтах от начала представления.|  
  
## Пример  
 В следующем примере показано, как использовать объект DataView для обработки двоичных данных, полученных от запроса XmlHttpRequest:  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var ints = new Int32Array(dataView.byteLength / 4);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getInt32(i * 4);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## Требования  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]