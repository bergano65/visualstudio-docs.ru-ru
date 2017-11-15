---
title: "Создание объектов (JavaScript) | Документы Майкрософт"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- constructors, including properties and methods
- function constructor
- creating objects, constructor functions
- constructor functions
- prototype objects
- creating objects
- custom objects, creating
- creating objects, about creating objects
- objects, creating [JavaScript]
- creating objects, prototypes
- custom objects
- initializing objects, using constructors
ms.assetid: 58d1baa5-4fe8-4a56-a926-5b11765df704
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0ba7962179cc2f0fcb972caee692edabee368c7d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="creating-objects-javascript"></a>Создание объектов (JavaScript)
Существует несколько способов создания собственных объектов в JavaScript. Вы можете непосредственно создать экземпляр [объекта Object](../javascript/reference/object-object-javascript.md) и добавить свои собственные свойства и методы, определить объект с помощью нотации объектного литерала, а также использовать для определения объекта функцию конструктора. Подробнее об использовании функций конструкторов: [Использование конструкторов для определения типов](../javascript/advanced/using-constructors-to-define-types.md).  
  
## <a name="example"></a>Пример  
 В следующем коде показано, как создать экземпляр объекта и добавить несколько свойств. В данном случае только объект `pasta` имеет свойства `grain`, `width` и `shape`.  
  
```JavaScript  
const pasta = new Object();  
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
  
## <a name="object-literals"></a>Объектные литералы  
 Если нужно создать только один экземпляр объекта, можно воспользоваться нотацией объектного литерала. В следующем коде показано, как создать экземпляр объекта с помощью нотации объектного литерала.  
  
```JavaScript  
const pasta = {  
    grain: "wheat",  
    width: 0.5,  
    shape: "round"  
};  
```  
  
 Объектный литерал можно также вставлять в конструктор.  
  
> [!CAUTION]
>  Описанные ниже функции поддерживаются только в [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)].  
  
 В [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)] для создания литерала объекта можно использовать сокращенный синтаксис.  
  
```JavaScript  
const key = 'a';  
const value = 5;  
  
// Older version  
const obj1 = {  
    key: key,  
    value: value  
};  
  
// Edge mode  
const obj2 = {key, value};  
  
console.log(obj2);  
  
// Output:  
// [object Object] {key: "a", value: 5}  
```  
  
 В следующем примере кода показано, как использовать сокращенный синтаксис для определения методов в объектных литералах.  
  
```JavaScript  
// Older versions  
const obj = {  
    method1: function() {},  
    method2: function() {}  
};  
  
// Edge mode  
const obj = {  
    method1() {},  
    method2() {}  
};  
```  
  
 В [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)] имена свойств в литералах объектов можно создавать динамически. В следующем примере кода имя свойства для объекта создается динамически с помощью синтаксиса set.  
  
```JavaScript  
const propName = "prop_42";  
  
const obj = {  
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
  
```JavaScript  
const propName = "prop_42";  
  
const obj = {  
    get [propName]() {  
        return 777;  
    }  
}  
  
console.log(obj.prop_42);  
  
// Output:  
// 777  
```  
  
 В следующем примере кода создается вычисляемое свойство и используется [синтаксис функции со стрелкой](../javascript/functions-javascript.md) для добавления 42 к имени свойства.  
  
```JavaScript  
const obj = {  
    [ 'prop_' + (() => 42)() ]: 42  
};  
```
