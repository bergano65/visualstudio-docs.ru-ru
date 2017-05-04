---
title: "Метод slice (ArrayBuffer) | Microsoft Docs"
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
ms.assetid: 2dcc51ff-f444-4d51-80ba-3bcd845ba0ae
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Метод slice (ArrayBuffer)
Возвращает фрагмент массива [ArrayBuffer](../../javascript/reference/arraybuffer-object.md).  
  
## Синтаксис  
  
```  
arrayBufferObj.slice(start, [end])   
```  
  
## Параметры  
 `arrayBufferObj`  
 Обязательный.  Объект [ArrayBuffer](../../javascript/reference/arraybuffer-object.md), из которого будет скопирован сегмент.  
  
 `start`  
 Обязательный.  Индекс байта начала копируемого фрагмента.  
  
 `end`  
 Необязательный.  Индекс байта конца копируемого фрагмента.  
  
## Заметки  
 Метод `slice` возвращает объект [ArrayBuffer](../../javascript/reference/arraybuffer-object.md), содержащий указанную часть объекта `arrayBufferObj`.  
  
 Метод `slice` выполняет копирование сегмента до байта, указанного параметром `end`, но не включая его.  Если значение параметра `start` или `end` отрицательное, указанный индекс обрабатывается как `length` \+ `start` или `end` соответственно, где `length` соответствует длине буфера [ArrayBuffer](../../javascript/reference/arraybuffer-object.md).  Если параметр `end` не задан, извлечение продолжается до конца объекта `arrayBufferObj`.  Если параметр `end` предшествует параметру `start`, байты в новый буфер [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) не копируются.  
  
## Пример  
 В следующем примере демонстрируется использование метода `slice`.  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer1 = req.response;  
            var buffer2 = buffer1.slice(40, 48);  
            var dataview = new DataView(buffer2);  
            var ints = new Int32Array(buffer2.byteLength / 4);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getInt32(i * 4);  
            }  
        alert(ints[1]);  
        }  
    }  
```  
  
## Требования  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## См. также  
 [Объект ArrayBuffer](../../javascript/reference/arraybuffer-object.md)