---
title: "Создание объектов (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "функции конструирования"
  - "конструкторы, включение свойств и методов"
  - "создание объектов"
  - "создание объектов, сведения о создании объектов"
  - "создание объектов, функции конструирования"
  - "создание объектов, прототипы"
  - "пользовательские объекты"
  - "пользовательские объекты, создание"
  - "функции конструирования"
  - "инициализация объектов, использование конструкторов"
  - "объекты, создание [JavaScript]"
  - "объекты-прототипы"
ms.assetid: 58d1baa5-4fe8-4a56-a926-5b11765df704
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# Создание объектов (JavaScript)
Существует несколько способов создания собственных объектов в JavaScript.  Можно создать экземпляр объекта [Объект Object](../javascript/reference/object-object-javascript.md) напрямую и добавить собственные свойства и методы,  определить объект с помощью нотации литерала объекта,  а также использовать для определения объекта функцию конструктора.  Дополнительные сведения об использовании функций конструкторов в статье [Использование конструкторов для определения типов](../javascript/advanced/using-constructors-to-define-types.md).  
  
## Пример  
 В следующем коде показано, как создать экземпляр объекта и добавить несколько свойств.  В данном случае только объект `pasta` имеет свойства `grain`, `width` и `shape`.  
  
```javascript  
var pasta = new Object();  
pasta.grain = "wheat";  
pasta.width = 0.5;  
pasta.shape = "round";  
pasta.getShape = function() {   
    return this.shape;   
};  
document.write(pasta.grain);  
document.write("<br/>");  
document.write(pasta.getShape());  
  
// Output:  
// wheat  
// round  
  
```  
  
## Литералы объектов  
 Если нужно создать только один экземпляр объекта, можно воспользоваться нотацией литерала объекта.  В следующем коде показано, как создать экземпляр объекта с помощью нотации литерала объекта.  
  
```javascript  
var pasta = {  
    grain: "wheat",  
    width: 0.5,  
    shape: "round"  
};  
```  
  
 Литерал объекта можно также вставлять в конструктор.  
  
> [!CAUTION]
>  Описанные ниже функции поддерживаются только в [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)].  
  
 В [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)] для создания литерала объекта можно использовать сокращенный синтаксис.  
  
```javascript  
var key = 'a';  
var value = 5;  
  
// Older version  
var obj1 = {  
    key: key,  
    value: value  
};  
  
// Edge mode  
var obj2 = {key, value};  
  
console.log(obj2);  
  
// Output:  
// [object Object] {key: "a", value: 5}  
```  
  
 В следующем примере кода показано, как использовать сокращенный синтаксис для определения методов в литералах объектов.  
  
```javascript  
// Older versions  
var obj = {  
    method1: function() {},  
    method2: function() {}  
};  
  
// Edge mode  
var obj = {  
    method1() {},  
    method2() {}  
};  
```  
  
 В [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)] имена свойств в литералах объектов можно создавать динамически.  В следующем примере кода имя свойства для объекта создается динамически с помощью синтаксиса set.  
  
```javascript  
var propName = "prop_42";  
  
var obj = {  
    value: 0,  
    set [propName](v) {  
        this.value = v;  
    }  
}  
  
console.log(obj.value);  
// Runs the setter property.  
obj.prop_42 = 777;  
console.log(obj.value);  
  
// Output:  
// 0  
// 777  
  
```  
  
 В следующем примере кода имя свойства для класса создается динамически с помощью синтаксиса get.  
  
```javascript  
var propName = "prop_42";  
  
var obj = {  
    get [propName]() {  
        return 777;  
    }  
}  
  
console.log(obj.prop_42);  
  
// Output:  
// 777  
```  
  
 В следующем примере кода создается вычисляемое свойство с помощью [синтаксиса функции со стрелкой](../javascript/functions-javascript.md), прибавляющей к имени свойства 42.  
  
```javascript  
var obj = {  
    [ 'prop_' + (() => 42)() ]: 42  
};  
```