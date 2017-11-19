---
title: "Объект ArrayBuffer | Документы Microsoft"
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
ms.assetid: 9fda1261-f450-493b-b3db-ecfa9ca93cd7
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c253d63d12a4a5e71d1661aae560b74debecdd62
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="arraybuffer-object"></a>Объект ArrayBuffer
Представляет необработанный буфер двоичных данных, который используется для хранения данных для разных типизированных массивов. `ArrayBuffers`Невозможно чтение и запись напрямую, но могут передаваться в типизированный массив или [объекта DataView](../../javascript/reference/dataview-object.md) для интерпретации необработанного буфера по мере необходимости.  
  
 Дополнительные сведения о типизированных массивов см. в разделе [типизированные массивы](../../javascript/advanced/typed-arrays-javascript.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```JavaScript  
  
arrayBuffer = new ArrayBuffer(length);  
```  
  
## <a name="parameters"></a>Параметры  
 `arrayBuffer`  
 Обязательный. Имя переменной, которой присваивается объект `ArrayBuffer`.  
  
 `length`  
 Длина буфера. Содержимое буфера ArrayBuffer инициализируется значением 0. Если запрошенное число байтов не удалось выделить, возникает исключение.  
  
## <a name="properties"></a>Свойства  
 В следующей таблице перечислены свойства объекта `ArrayBuffer`.  
  
|Свойство|Описание|  
|--------------|-----------------|  
|[Свойство byteLength](../../javascript/reference/bytelength-property-arraybuffer.md)|Только для чтения. Длина буфера ArrayBuffer (в байтах).|  
  
## <a name="functions"></a>Функции  
 В следующей таблице перечислены функции объекта `ArrayBuffer`.  
  
|Свойство|Описание|  
|--------------|-----------------|  
|[Функция ArrayBuffer.isView](../../javascript/reference/arraybuffer-isview-function-arraybuffer.md)|Определяет, обеспечивает ли объект представление буфера.|  
  
## <a name="methods"></a>Методы  
 В следующей таблице перечислены методы объекта `ArrayBuffer`.  
  
|Свойство|Описание|  
|--------------|-----------------|  
|[Метод slice](../../javascript/reference/slice-method-arraybuffer.md)|Возвращает фрагмент буфера `ArrayBuffer`.|  
  
## <a name="example"></a>Пример  
 В следующем примере показано использование объекта ArrayBuffer для обработки двоичных данных, полученных из [XMLHttpRequest](http://msdn.microsoft.com/library/ie/ms535874\(v=vs.85\).aspx). Можно использовать [объекта DataView](../../javascript/reference/dataview-object.md) для получения отдельных значений.  
  
```JavaScript  
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
  
## <a name="remarks"></a>Примечания  
 Дополнительные сведения об использовании `XmlHttpRequest`, в разделе [улучшения объекта XMLHttpRequest](http://msdn.microsoft.com/en-us/be09137c-6546-441b-b953-dcbf72b77069).  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]