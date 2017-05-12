---
title: "Функция Object.getOwnPropertyDescriptor (JavaScript) | Microsoft Docs"
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
helpviewer_keywords: 
  - "getOwnPropertyDescriptor - метод [JavaScript]"
ms.assetid: 8f0e1c90-c4f9-44c4-bf76-726bacecbc14
caps.latest.revision: 45
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 45
---
# Функция Object.getOwnPropertyDescriptor (JavaScript)
Возвращает дескриптор собственного свойства указанного объекта.  Дескриптор собственного свойства определяется в самом объекте, а не наследуется от прототипа.  
  
## Синтаксис  
  
```  
Object.getOwnPropertyDescriptor(object, propertyname)  
```  
  
## Параметры  
 `object`  
 Обязательный.  Объект, содержащий свойство.  
  
 `propertyname`  
 Обязательный.  Имя свойства.  
  
## Возвращаемое значение  
 Дескриптор свойства.  
  
## Заметки  
 Функция `Object.getOwnPropertyDescriptor` позволяет получить объект дескриптора, описывающий атрибуты свойства.  
  
 [Функция Object.defineProperty](../../javascript/reference/object-defineproperty-function-javascript.md) используется для добавления или изменения свойств.  
  
## Пример свойства данных  
 Код в следующем примере возвращает дескриптор свойства данных и использует его, чтобы сделать свойство доступным только для чтения.  
  
```javascript  
// Create a user-defined object.  
var obj = {};  
  
// Add a data property.  
obj.newDataProperty = "abc";  
  
// Get the property descriptor.  
var descriptor = Object.getOwnPropertyDescriptor(obj, "newDataProperty");  
  
// Change a property attribute.  
descriptor.writable = false;  
Object.defineProperty(obj, "newDataProperty", descriptor);  
  
```  
  
 Чтобы вывести список атрибутов свойства, добавьте к примеру следующий код.  
  
```javascript  
// Get the descriptor from the object.  
var desc2 = Object.getOwnPropertyDescriptor(obj, "newDataProperty");  
  
// List the descriptor attributes.  
for (var prop in desc2) {  
    document.write(prop + ': ' + desc2[prop]);  
    document.write("<br />");  
}  
  
// Output:  
// value: abc  
// writable: false  
// enumerable: true  
// configurable: true  
```  
  
## Требования  
 [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)] поддерживает все функции.  
  
 [!INCLUDE[jsv58textspecific](../../javascript/reference/includes/jsv58textspecific-md.md)] поддерживает объекты DOM, но не поддерживает пользовательские объекты.  Атрибуты `enumerable` и `configurable` могут быть заданы, но не используются.  
  
## См. также  
 [Прототипы модели DOM. Часть 2: поддержка методов доступа \(getter\/setter\)](http://msdn.microsoft.com/library/dd229916\(v=VS.85\).aspx)   
 [Функция Object.defineProperty](../../javascript/reference/object-defineproperty-function-javascript.md)