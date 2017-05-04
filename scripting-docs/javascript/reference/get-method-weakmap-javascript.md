---
title: "Метод get (WeakMap) (JavaScript) | Microsoft Docs"
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
ms.assetid: d922c55d-486d-4feb-aedc-1f4867c417d2
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Метод get (WeakMap) (JavaScript)
Возвращает указанный элемент из объекта `WeakMap`.  
  
## Синтаксис  
  
```javascript  
weakmapObj.get(key)  
```  
  
#### Параметры  
 `weakmapObj`  
 Обязательное.  Объект `WeakMap`.  
  
 `key`  
 Обязательное.  Ключ элемента в `WeakMap`.  
  
## Значение свойства или возвращаемое значение  
 Возвращает объект, связанный с ключом.  Если `WeakMap` не содержит ключ, этот метод возвращает значение `undefined`.  
  
## Пример  
 В следующем примере показано, как извлечь члены из объекта `WeakMap`.  
  
```javascript  
var dog = {  
    breed: "yorkie"  
}  
  
var cat = {  
    breed: "burmese"  
}  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
wm.set(cat, "pepper");  
  
document.write(wm.get(dog) + ": ");  
document.write(dog.breed);  
document.write("<br />");  
document.write(wm.get(cat) + ": ");  
document.write(cat.breed);  
  
// Output:  
// fido: yorkie  
// pepper: burmese  
  
```  
  
## Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]