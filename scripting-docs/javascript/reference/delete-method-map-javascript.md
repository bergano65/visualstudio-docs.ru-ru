---
title: "Метод delete (Map) (JavaScript) | Microsoft Docs"
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
ms.assetid: a073e1a1-5862-485b-b2bd-26c66a3aff51
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Метод delete (Map) (JavaScript)
Удаляет указанный элемент из карты.  
  
## Синтаксис  
  
```javascript  
mapObj.delete(key)  
```  
  
#### Параметры  
 `mapObj`  
 Обязательное.  Объект `Map`.  
  
 `key`  
 Обязательное.  Ключ удаляемого элемента.  
  
## Значение свойства или возвращаемое значение  
 Значение `true`, если элемент удален.  
  
## Пример  
 В следующем примере показано, как добавить члены в `Map` и затем удалить один из них.  
  
```javascript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
m.delete(1);  
  
m.forEach(function (item) {  
    document.write(item.toString() + "<br />");  
});  
  
// Output:  
// red  
// 2  
```  
  
## Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]