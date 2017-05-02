---
title: "Метод has (WeakMap) (JavaScript) | Microsoft Docs"
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
ms.assetid: 12bedca1-bde7-413a-a4e2-06c03559044f
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Метод has (WeakMap) (JavaScript)
Возвращает значение `true`, если объект `WeakMap` содержит указанный элемент.  
  
## Синтаксис  
  
```javascript  
weakmapObj.has(key)  
```  
  
#### Параметры  
 `weakmapObj`  
 Обязательное.  Объект `WeakMap`.  
  
 `key`  
 Обязательное.  Ключ элемента, который требуется протестировать.  
  
## Значение свойства или возвращаемое значение  
 Значение `true`, если `WeakMap` содержит указанный ключ.  
  
## Пример  
 В следующем примере показано добавление члена в `WeakMap` и использование для проверки наличия `has`.  
  
```javascript  
var dog = {  
    breed: "yorkie"  
}  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
  
document.write(wm.has(dog));  
  
// Output:  
// true  
```  
  
## Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]