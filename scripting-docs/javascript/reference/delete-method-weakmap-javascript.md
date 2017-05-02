---
title: "Метод delete (WeakMap) (JavaScript) | Microsoft Docs"
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
ms.assetid: 7d54ae55-e514-45ba-b403-d1eee46837d2
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Метод delete (WeakMap) (JavaScript)
Удаляет указанный элемент из объекта `WeakMap`.  
  
## Синтаксис  
  
```javascript  
weakmapObj.delete(key)  
```  
  
#### Параметры  
 `weakmapObj`  
 Обязательное.  Объект `WeakMap`.  
  
 `key`  
 Обязательное.  Ключ удаляемого элемента.  
  
## Значение свойства или возвращаемое значение  
 Значение `true`, если элемент удален.  
  
## Пример  
 В следующем примере показано, как добавить член в `WeakMap` и затем удалить его.  
  
```javascript  
function Dog(breed) {  
    this.breed = breed;  
}  
  
var dog = new Dog("yorkie");  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
wm.delete(dog);  
```  
  
## Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]