---
title: "Метод getFloat32 (DataView) | Microsoft Docs"
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
ms.assetid: adecf671-bde4-46be-a875-33b6d6e970b1
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Метод getFloat32 (DataView)
Получает значение Float32 по указанному смещению в байтах от начала представления.  Ограничения по выравниванию отсутствуют; многобайтовые значения могут извлекаться по любому смещению.  
  
## Синтаксис  
  
```  
var testFloat = dataView.getFloat32(byteOffset, littleEndian);   
```  
  
## Параметры  
 `testFloat`  
 Обязательный.  Значение Float32, возвращаемое из метода.  
  
 `byteOffset`  
 Место в буфере, откуда следует извлечь значение.  
  
 `littleEndian`  
 Необязательный.  Если этот аргумент имеет значение undefined, считывается значение с обратным порядком байтов, в противном случае — значение с прямым порядком байтов.  
  
## Заметки  
 При чтении за пределами представления эти методы вызывают исключение.  
  
## Пример  
 В следующем примере показано, как получить первое значение Float32 в DataView.  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            alert(dataView.getFloat32(0));  
        }  
    }  
  
```  
  
## Требования  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]