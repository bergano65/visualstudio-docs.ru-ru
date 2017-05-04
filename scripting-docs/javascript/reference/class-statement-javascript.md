---
title: "Оператор class (JavaScript) | Microsoft Docs"
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
ms.assetid: bf45ebad-4678-4062-88df-55d32b603c69
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Оператор class (JavaScript)
Объявляет новый класс.  
  
## Синтаксис  
  
```  
class classname () [extends object] {  
    [constructor([arg1 [,... [,argN]]]) {  
        statements  
    }]  
    [[static] method([arg1 [,... [,argN]]]) {  
        statements  
    }]  
}  
```  
  
#### Параметры  
 `classname`  
 Обязательный.  Имя класса.  
  
 `object`  
 Необязательный.  Объект или класс, от которого новый класс наследует свойства и методы.  
  
 `constructor`  
 Необязательный.  Функция конструктора, которая инициализирует новый экземпляр класса.  
  
 `arg1...argN`  
 Необязательный.  Вспомогательный список аргументов, которые понимает данная функция, разделенных запятыми.  
  
 `statements`  
 Необязательный.  Один или несколько операторов [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
 `static`  
 Необязательный.  Указывает статический метод.  
  
 `method`  
 Необязательный.  Один или несколько экземпляров или статических методов [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], которые могут быть вызваны для экземпляра класса.  
  
## Заметки  
 Класс позволяет создавать новые объекты, используя наследование на основе прототипа, конструкторы, методы экземпляров и статические методы.  Объект `super` в конструкторе или методе класса позволяет вызывать такой же конструктор или метод, как и в родительском классе или объекте.  Чтобы указать, методы какого класса или объекта должен унаследовать новый класс, добавьте после имени класса оператор `extends`.  
  
## Пример  
  
```javascript  
class Spelunking extends EXPERIENCE.Outdoor {  
  constructor(name, location) {  
    super(name, location);  
  
    this.minSkill = Spelunking.defaultSkill();  
    //...  
  }  
  update(minSkill) {  
    //...  
    super.update(minSkill);  
  }  
  static defaultSkill() {  
    return new EXPERIENCE.Level3();  
  }  
}  
```  
  
## Пример  
 Для классов можно также создавать имена вычисляемых свойств.  В следующем примере кода имя вычисляемого свойства создается с помощью синтаксиса `set`.  
  
```javascript  
var propName = "prop_42";  
  
class Spelunking {  
    set [propName](v) {  
        this.value = v;  
    }  
};  
  
var s = new Spelunking();  
console.log(s.value);  
s.prop_42 = 42;  
console.log(s.value);  
  
// Output:  
// undefined  
// 42  
  
```  
  
## Пример  
 В следующем примере кода имя свойства для класса создается динамически с помощью синтаксиса `get`.  
  
```javascript  
var propName = "prop_42";  
  
class Spelunking {  
    get [propName]() {  
        return 777;  
    }  
}  
  
var s = new Spelunking();  
console.log(s.prop_42);  
  
// Output:  
// 777  
```  
  
## Требования  
 [!INCLUDE[jsv12exp](../../javascript/reference/includes/jsv12exp-md.md)]