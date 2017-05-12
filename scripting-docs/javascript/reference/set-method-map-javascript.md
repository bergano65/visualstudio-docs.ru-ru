---
title: "Метод set (Map) (JavaScript) | Microsoft Docs"
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
ms.assetid: 31ee71a0-b09d-442a-9e02-825accf94ffa
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Метод set (Map) (JavaScript)
Добавляет новый элемент в сопоставление.  
  
## Синтаксис  
  
```javascript  
mapObj.set(key, value)  
```  
  
#### Параметры  
 `mapObj`  
 Обязательный.  Объект `Map`.  
  
 `key`  
 Обязательный.  Ключ для нового элемента.  
  
 `value`  
 Обязательный.  Добавляемое значение элемента.  
  
## Значение свойства, возвращаемое значение  
 Возвращает объект `Map`, содержащий новую пару "ключ\-значение".  
  
## Заметки  
 При добавлении значения в коллекцию с помощью существующего ключа новое значение заменяет старое.  
  
## Пример  
 В следующем примере показано добавление членов в объект `Map` и затем извлечение их.  
  
```javascript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
  
m.forEach(function (item) {  
    document.write(item.toString() + "<br />");  
});  
  
// Output:  
// black  
// red  
// 2  
```  
  
## Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]