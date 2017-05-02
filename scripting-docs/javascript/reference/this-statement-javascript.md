---
title: "Оператор this (JavaScript) | Microsoft Docs"
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
  - "this_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "конструкторы, ссылка на текущий объект"
  - "this - оператор"
ms.assetid: 8510a00b-2f14-4700-a276-4d9a523c5112
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Оператор this (JavaScript)
Ссылается на текущий объект.  
  
## Синтаксис  
  
```  
this.property  
```  
  
## Заметки  
 Обязательный аргумент `property` — одно из свойств текущего объекта  
  
 Ключевое слово `this` можно использовать в конструкторах объекта для ссылки на текущий объект.  
  
## Пример  
 В следующем примере **this** ссылается на вновь созданный объект Car и присваивает значения трем свойствам:  
  
```javascript  
function Car(color, make, model){  
   this.color = color;  
   this.make = make;  
   this.model = model;  
}  
```  
  
 Ключевое слово **this** обычно ссылается на объект **window**, если оно используется вне области любого другого объекта.  Однако внутри обработчиков событий `this` ссылается на элемент DOM, вызвавший событие.  
  
 В следующем коде \(для Internet Explorer 9 и более поздних версий\) обработчик событий выводит строковую версию кнопки, которая имеет идентификатор элемента "clicker".  
  
```javascript  
document.getElementById("clicker").addEventListener("click", eventHandler, false);  
  
        function eventHandler(ev) {  
            document.write(this.toString());  
        }  
  
// Output (when you click the button): [object HTMLButtonElement]  
  
```  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## См. также  
 [Оператор new](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Использование метода bind](../../javascript/advanced/using-the-bind-method-javascript.md)