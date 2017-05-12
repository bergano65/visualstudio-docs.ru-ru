---
title: "Свойство prototype (String) | Microsoft Docs"
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
ms.assetid: 437ce478-9c45-45f7-8952-bd71856cfcd8
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Свойство prototype (String)
Возвращает ссылку на прототип класса строки.  
  
## Синтаксис  
  
```  
  
string.prototype  
```  
  
## Заметки  
 Аргумент типа `string` представляет имя строки.  
  
 Свойство `prototype` используется для предоставления базового набора функциональных возможностей классу объектов.  Новые экземпляры объекта наследуют поведение прототипа, присвоенного этому объекту.  
  
 Например, чтобы добавить в объект `String` метод, возвращающий значение последнего элемента строки, объявите функцию, добавьте ее в свойство `String.prototype`, а затем используйте ее.  
  
```javascript  
function string_last( ){  
    return this.charAt(this.length - 1);  
}  
String.prototype.last = string_last;  
var myString = new String("every good boy does fine");  
document.write(myString.last());  
  
// Output:  
// e  
```  
  
 Все встроенные объекты [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] имеют свойство `prototype`, которое доступно только для чтения.  К прототипу можно добавлять свойства и методы, но невозможно присвоить объекту другой прототип.  Однако пользовательским объектам можно присваивать новый прототип.  
  
 В списках методов и свойств для каждого встроенного объекта, содержащихся в данном справочнике по языку, указано, какие члены принадлежат прототипу объекта, а какие нет.  
  
## Требования  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]