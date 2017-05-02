---
title: "Свойство __proto__ (Object) (JavaScript) | Microsoft Docs"
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
  - "__proto__"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 97c3f84d-125e-4905-b921-b021264964ee
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Свойство __proto__ (Object) (JavaScript)
Содержит Ссылку на внутренний прототип, содержащий указанный объект.  
  
## Синтаксис  
  
```  
object.__proto__  
```  
  
#### Параметры  
 `object`  
 Обязательное.  Объект, для которого требуется задать прототип.  
  
## Заметки  
 Свойство `__proto__` можно использовать для задания прототипа объекта.  
  
 Объект или функция наследуют все методы и свойства нового прототипа вместе со всеми методами и свойствами в цепочке прототипов нового прототипа.  Объект может иметь только один прототип \(не включая наследуемые прототипы в цепочке прототипов\), поэтому при вызове свойства `__proto__` следует заменить предыдущий прототип.  
  
 можно задать прототип только в расширяемом объекте.  Дополнительные сведения см. в разделе [Функция Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md).  
  
> [!NOTE]
>  Имя свойства `__proto__` начинается и заканчивается двумя символами подчеркивания.  
  
## Пример  
 В следующем примере показано, как задать прототип для объекта.  
  
```javascript  
function Rectangle() {  
}  
  
var rec = new Rectangle();  
  
if (console && console.log) {  
    console.log(rec.__proto__ === Rectangle.prototype);  // Returns true  
    rec.__proto__ = Object.prototype;  
    console.log(rec.__proto__ === Rectangle.prototype);  // Returns false  
}  
```  
  
## Пример  
 В следующем примере кода показано добавление свойств в объект путем добавления их в прототип.  
  
```javascript  
var proto = { y: 2 };  
  
var obj = { x: 10 };  
obj.__proto__ = proto;  
  
proto.y = 20;  
proto.z = 40;  
  
if (console && console.log) {  
    console.log(obj.x === 10);  // Returns true  
    console.log(obj.y === 20);  // Returns true  
    console.log(obj.z === 40);  // Returns true  
}  
```  
  
## Пример  
 Следующий пример кода добавляет свойства в объект `String` путем задания в нем нового прототипа.  
  
```javascript  
var stringProp = { desc: "description" };  
  
String.__proto__ = stringProp;  
var s1 = "333";  
var s2 = new String("333");  
  
if (console && console.log) {  
  
    console.log(String.desc === "description"); // Returns true  
    console.log(s1.desc === "description");     // Returns false  
    console.log(s2.desc === "description");     // Returns false  
  
    s1.__proto__ = String;  // Can't be set.  
    s2.__proto__ = String;  
  
    console.log(s1.desc === "description"); // Returns false  
    console.log(s2.desc === "description"); // Returns true  
}  
```  
  
## Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## См. также  
 [Прототипы и их наследование](../../javascript/advanced/prototypes-and-prototype-inheritance.md)