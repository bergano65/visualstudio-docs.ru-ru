---
title: "Метод setInt32 (DataView) | Microsoft Docs"
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
ms.assetid: 07e5f068-0e3f-4c23-84b3-c72658d7f194
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Метод setInt32 (DataView)
Задает значение Int32 по указанному смещению в байтах от начала представления.  Ограничения по выравниванию отсутствуют; многобайтовые значения могут задаваться по любому смещению.  
  
## Синтаксис  
  
```  
dataView.setInt32 (byteOffset, value, littleEndian);   
```  
  
## Параметры  
 `byteOffset`  
 Место в буфере, откуда следует извлечь значение.  
  
 `value`  
 Задаваемое значение.  
  
 `littleEndian`  
 Необязательный.  Если этот параметр имеет значение false или undefined, записывается значение с обратным порядком байтов, в противном случае — значение с прямым порядком байтов.  
  
## Заметки  
 При записи за пределами представления эти методы вызывают исключение.  
  
## Пример  
 В следующем примере показано, как задать первое значение Int32 в DataView.  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            dataView.setInt32(0, 9);  
        }  
    }  
  
```  
  
## Требования  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]