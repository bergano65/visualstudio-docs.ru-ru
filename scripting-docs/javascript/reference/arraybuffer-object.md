---
title: "Объект ArrayBuffer | Microsoft Docs"
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
ms.assetid: 9fda1261-f450-493b-b3db-ecfa9ca93cd7
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Объект ArrayBuffer
Представляет необработанный буфер двоичных данных, который используется для хранения данных для разных типизированных массивов.  Буферы `ArrayBuffers` не поддерживают прямое чтение и запись данных, однако их можно передать в типизированный массив или представление [Объект DataView](../../javascript/reference/dataview-object.md) для интерпретации необработанного буфера по мере необходимости.  
  
 Дополнительные сведения о типизированных массивах см. в разделе [Типизированные массивы](../../javascript/advanced/typed-arrays-javascript.md).  
  
## Синтаксис  
  
```javascript  
  
arrayBuffer = new ArrayBuffer(length);  
```  
  
## Параметры  
 `arrayBuffer`  
 Обязательный.  Имя переменной, которой присваивается объект `ArrayBuffer`.  
  
 `length`  
 Длина буфера.  Содержимое буфера ArrayBuffer инициализируется значением 0.  Если запрошенное число байтов не удалось выделить, возникает исключение.  
  
## Свойства  
 В следующей таблице перечислены свойства объекта `ArrayBuffer`.  
  
|Свойство|Описание|  
|--------------|--------------|  
|[Свойство byteLength](../../javascript/reference/bytelength-property-arraybuffer.md)|Только для чтения.  Длина буфера ArrayBuffer \(в байтах\).|  
  
## Функции  
 В следующей таблице перечислены функции объекта `ArrayBuffer`.  
  
|Свойство|Описание|  
|--------------|--------------|  
|[Функция ArrayBuffer.isView](../../javascript/reference/arraybuffer-isview-function-arraybuffer.md)|Определяет, обеспечивает ли объект представление буфера.|  
  
## Методы  
 В следующей таблице перечислены методы объекта `ArrayBuffer`.  
  
|Свойство|Описание|  
|--------------|--------------|  
|[Метод slice](../../javascript/reference/slice-method-arraybuffer.md)|Возвращает фрагмент буфера `ArrayBuffer`.|  
  
## Пример  
 В следующем примере показано использование объекта ArrayBuffer для обработки двоичных данных, полученных из запроса [XMLHttpRequest](http://msdn.microsoft.com/library/ie/ms535874\(v=vs.85\).aspx).  Для получения отдельных значений можно использовать объект [Объект DataView](../../javascript/reference/dataview-object.md).  
  
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
  
## Заметки  
 Дополнительные сведения об использовании `XmlHttpRequest` см. в разделе [XMLHttpRequest enhancements](http://msdn.microsoft.com/ru-ru/be09137c-6546-441b-b953-dcbf72b77069).  
  
## Требования  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]