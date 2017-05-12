---
title: "Свойство constructor (Object) (JavaScript) | Microsoft Docs"
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
  - "constructor"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "constructor - свойство"
ms.assetid: 6f5d0e9d-e85f-4fde-b558-744510483d69
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Свойство constructor (Object) (JavaScript)
Задает функцию, которая создает объект.  
  
## Синтаксис  
  
```  
  
object.constructor  
```  
  
## Заметки  
 Необходимый параметр `object` представляет собой имя объекта или функции.  
  
 Свойство `constructor` является членом прототипа каждого объекта, у которого есть прототип.  Это включает все встроенные объекты [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], за исключением объектов `Global` и `Math`.  Свойство `constructor` содержит ссылку на функцию, которая создает экземпляры данного конкретного объекта.  
  
## Пример  
 В следующем примере кода демонстрируется использование свойства constructor.  
  
```javascript  
// A constructor function.  
function MyObj() {  
    this.number = 1;  
}  
  
var x = new String("Hi");  
  
if (x.constructor == String)  
    document.write("Object is a String.");  
document.write ("<br />");  
  
var y = new MyObj;  
if (y.constructor == MyObj)  
    document.write("Object constructor is MyObj.");  
  
// Output:  
// Object is a String.  
// Object constructor is MyObj.  
  
```  
  
## Требования  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## См. также  
 [Свойство prototype \(Object\)](../../javascript/reference/prototype-property-object-javascript.md)