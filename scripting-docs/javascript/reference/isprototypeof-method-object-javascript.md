---
title: "Метод isPrototypeOf (Object) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "isPrototypeOf"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "isPrototypeOf - метод"
ms.assetid: 9c821319-c208-480f-915e-565ef6e017b6
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Метод isPrototypeOf (Object) (JavaScript)
Определяет, существует ли объект в цепочке прототипов другого объекта.  
  
## Синтаксис  
  
```  
  
prototype.isPrototypeOf(object)  
```  
  
## Параметры  
 `prototype`  
 Обязательный.  Прототип объекта.  
  
 `object`  
 Обязательный.  Другой объект, цепочку прототипов которого требуется проверить.  
  
## Заметки  
 Метод `isPrototypeOf` возвращает значение `true`, если `object` содержит `prototype` в своей цепочке прототипов.  Цепочка прототипов служит для совместного использования функциональных возможностей несколькими экземплярами одного типа объектов.  Метод `isPrototypeOf` возвращает значение `false`, если `object` не является объектом или если `prototype` отсутствует в цепочке прототипов объекта `object`.  
  
## Пример  
 В следующем примере показано использование метода `isPrototypeOf`.  
  
```javascript  
function Rectangle() {  
}  
  
var rec = new Rectangle();  
  
document.write(Rectangle.prototype.isPrototypeOf(rec));  
  
// Output: true  
```  
  
## Требования  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## См. также  
 [Свойство prototype \(Object\)](../../javascript/reference/prototype-property-object-javascript.md)