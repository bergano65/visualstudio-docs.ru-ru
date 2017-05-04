---
title: "Метод set (WeakMap) (JavaScript) | Microsoft Docs"
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
ms.assetid: 29fc72b1-224f-4f19-8c06-5d926d695b03
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Метод set (WeakMap) (JavaScript)
Добавляет новый элемент в объект `WeakMap`.  
  
## Синтаксис  
  
```javascript  
weakmapObj.set(key, value)  
```  
  
#### Параметры  
 `weakmapObj`  
 Обязательный.  Объект `WeakMap`.  
  
 `key`  
 Обязательный.  Объект, представляющий ключ добавляемого элемента.  Это должна быть ссылка на объект.  
  
 `value`  
 Обязательный.  Добавляемое значение элемента.  
  
## Значение свойства, возвращаемое значение  
 Возвращает объект `WeakMap`, содержащий новую пару "ключ\-значение".  
  
## Заметки  
 При добавлении значения в коллекцию с помощью существующего ключа новое значение заменяет старое.  
  
## Пример  
 В следующем примере показано добавление членов в объект `WeakMap`.  
  
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
```  
  
## Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]