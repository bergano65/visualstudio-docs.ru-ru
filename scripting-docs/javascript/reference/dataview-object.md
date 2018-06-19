---
title: Объект DataView | Документы Microsoft
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
ms.assetid: 250ec067-7505-4ee0-82ab-bfd3c2820afa
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 370ee1afbdf7fe1d87843c4979833d54a575a4fd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637274"
---
# <a name="dataview-object"></a>Объект DataView
Объект DataView можно использовать для чтения и записи различных типов двоичных данных в любое место в буфере ArrayBuffer.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
dataView = new DataView(buffer, byteOffset, byteLength);  
```  
  
## <a name="parameters"></a>Параметры  
 `dataView`  
 Обязательный. Имя переменной, которой **DataView** присваивается объект.  
  
 `buffer`  
 Буфер ArrayBuffer, представляемый DataView.  
  
 `byteOffset`  
 Необязательно. Задает смещение в байтах от начала буфера, по которому должно начинаться DataView.  
  
 `byteLength`  
 Необязательно. Указывает длину (в байтах) буфера, который должен представлять DataView раздела.  
  
## <a name="remarks"></a>Примечания  
 Если не указано байтовое смещение и byteLength, DataView охватывает весь диапазон ArrayBuffer. Если byteLength опущено, DataView начиная с заданного байтовое смещение до конца буфера ArrayBuffer. Если данный байтовое смещение и byteLength ссылается на область за пределами буфера arraybuffer, возникает исключение.  
  
## <a name="properties"></a>Свойства  
 В следующей таблице перечислены свойства объекта `DataView`.  
  
|Свойство|Описание|  
|--------------|-----------------|  
|[Свойство buffer](../../javascript/reference/buffer-property-dataview.md)|Только для чтения. Получает буфер ArrayBuffer, на который ссылается это представление.|  
|[Свойство byteLength](../../javascript/reference/bytelength-property-dataview.md)|Только для чтения. Длина данного представления от начала его буфера ArrayBuffer в байтах, зафиксированная во время создания.|  
|[Свойство byteOffset](../../javascript/reference/byteoffset-property-dataview.md)|Только для чтения. Смещение от начала его буфера ArrayBuffer в байтах, зафиксированная во время создания этого представления.|  
  
## <a name="methods"></a>Методы  
 В следующей таблице перечислены методы объекта `DataView`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[Метод getInt8](../../javascript/reference/getint8-method-dataview.md)|Получает значение Int8 на указанное смещение в байтах от начала представления.|  
|[Метод getUint8 (DataView)](../../javascript/reference/getuint8-method-dataview.md)|Получает значение Uint8 на указанное смещение в байтах от начала представления.|  
|[Метод getInt16 (DataView)](../../javascript/reference/getint16-method-dataview.md)|Получает значение Int16 на указанное смещение в байтах от начала представления.|  
|[Метод getUint16 (DataView)](../../javascript/reference/getuint16-method-dataview.md)|Получает значение Uint16 на указанное смещение в байтах от начала представления.|  
|[Метод getInt32 (DataView)](../../javascript/reference/getint32-method-dataview.md)|Получает значение Int32 на указанное смещение в байтах от начала представления.|  
|[Метод getUint32 (DataView)](../../javascript/reference/getuint32-method-dataview.md)|Получает значение Uint32 на указанное смещение в байтах от начала представления.|  
|[Метод getFloat32 (DataView)](../../javascript/reference/getfloat32-method-dataview.md)|Получает значение Float32 на указанное смещение в байтах от начала представления.|  
|[Метод getFloat64 (DataView)](../../javascript/reference/getfloat64-method-dataview.md)|Получает значение Float64 на указанное смещение в байтах от начала представления.|  
|[Метод setInt8 (DataView)](../../javascript/reference/setint8-method-dataview.md)|Сохраняет значение Int8 на указанное смещение в байтах от начала представления.|  
|[Метод setUint8 (DataView)](../../javascript/reference/setuint8-method-dataview.md)|Сохраняет значение Uint8 на указанное смещение в байтах от начала представления.|  
|[Метод setInt16 (DataView)](../../javascript/reference/setint16-method-dataview.md)|Сохраняет значение Int16 на указанное смещение в байтах от начала представления.|  
|[Метод setUint16 (DataView)](../../javascript/reference/setuint16-method-dataview.md)|Сохраняет значение Uint16 на указанное смещение в байтах от начала представления.|  
|[Метод setInt32 (DataView)](../../javascript/reference/setint32-method-dataview.md)|Сохраняет значение Int32 на указанное смещение в байтах от начала представления.|  
|[Метод setUint32 (DataView)](../../javascript/reference/setuint32-method-dataview.md)|Сохраняет значение Uint32 на указанное смещение в байтах от начала представления.|  
|[Метод setFloat32 (DataView)](../../javascript/reference/setfloat32-method-dataview.md)|Сохраняет значение Float32 на указанное смещение в байтах от начала представления.|  
|[Метод setFloat64 (DataView)](../../javascript/reference/setfloat64-method-dataview.md)|Сохраняет значение Float64 на указанное смещение в байтах от начала представления.|  
  
## <a name="example"></a>Пример  
 В следующем примере показано использование объекта DataView для обработки двоичных данных, полученных из запроса XmlHttpRequest:  
  
```JavaScript  
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
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]