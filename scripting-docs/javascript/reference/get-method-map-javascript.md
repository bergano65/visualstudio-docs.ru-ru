---
title: "Метод get (Map) (JavaScript) | Microsoft Docs"
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
ms.assetid: bebbd6bc-6e61-4674-8196-7e907798973f
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Метод get (Map) (JavaScript)
Возвращает заданный элемент из сопоставления.  
  
## Синтаксис  
  
```javascript  
mapObj.get(key)  
```  
  
#### Параметры  
 `mapObj`  
 Обязательное.  Объект `Map`.  
  
 `key`  
 Обязательное.  Ключ элемента в `Map`.  
  
## Значение свойства или возвращаемое значение  
 Возвращает объект, связанный с ключом.  Если `Map` не содержит ключ, этот метод возвращает значение `undefined`.  
  
## Пример  
 В следующем примере показано, как извлечь элемент из объекта `Map`.  
  
```javascript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
  
document.write(m.get(2));  
  
// Output:  
// red  
  
```  
  
## Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]