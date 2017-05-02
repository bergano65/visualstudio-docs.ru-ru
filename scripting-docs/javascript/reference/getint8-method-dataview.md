---
title: "Метод getInt8 (DataView) | Microsoft Docs"
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
ms.assetid: 867eefa0-f2e0-44b9-85bc-efb849d55138
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Метод getInt8 (DataView)
Получает значение Int8 по указанному смещению в байтах от начала представления.  Ограничения по выравниванию отсутствуют; многобайтовые значения могут извлекаться по любому смещению.  
  
## Синтаксис  
  
```  
var testInt = dataView.getInt8(byteOffset);   
```  
  
## Параметры  
 `testInt`  
 Обязательный.  Значение Int8, возвращаемое из метода.  
  
 `byteOffset`  
 Место в буфере, откуда следует извлечь значение.  
  
## Заметки  
 При чтении за пределами представления эти методы вызывают исключение.  
  
## Пример  
 В следующем примере показано, как получить первое значение Int8 в DataView.  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            alert(dataView.getInt8(0));  
        }  
    }  
  
```  
  
## Требования  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]