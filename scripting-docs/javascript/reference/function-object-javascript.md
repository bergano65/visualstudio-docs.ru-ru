---
title: "Объект Function (JavaScript) | Microsoft Docs"
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
  - "function"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Function - объект"
ms.assetid: d3834767-203c-475e-848c-95c423ba15b6
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Объект Function (JavaScript)
Создает новую функцию.  
  
## Синтаксис  
  
```  
function functionName([argname1  [, ...[, argnameN]]])  
{  
   body  
}  
```  
  
## Синтаксис  
  
```  
  
functionName = new Function( [argname1,  [... argnameN,]] body );  
```  
  
## Параметры  
 `functionName`  
 Обязательный.  Имя новой созданной функции.  
  
 `argname1...argnameN`  
 Необязательный.  Список аргументов, принимаемых функцией.  
  
 `body`  
 Необязательный.  Строка, содержащая блок кода [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], который должен быть выполнен при вызове функции.  
  
## Заметки  
 Функция является базовым типом данных в [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  Синтаксис 1 создает значение функции, которое при необходимости преобразуется [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] в объект `Function`.  [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] преобразует объекты `Function`, созданные с синтаксисом 2, в значения функции при вызове этой функции.  
  
 Синтаксис 1 является стандартным способом создания новых функций в [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  Синтаксис 2 представляет собой альтернативную форму, служащую для создания объектов функции явным образом.  
  
 Например, чтобы объявить функцию, которая складывает два переданных ей аргумента, можно использовать один из двух способов:  
  
## Пример 1  
  
```javascript  
function add(x, y)  
{  
   return(x + y);  
}  
```  
  
## Пример 2  
  
```  
var add = function(x, y) {  
     return(x+y);  
}  
```  
  
 В обоих случаях функция вызывается с помощью строки кода, аналогичной следующей:  
  
```javascript  
add(2, 3);  
```  
  
> [!NOTE]
>  При вызове функции следует обязательно указывать скобки и все обязательные аргументы.  При вызове функции без скобок возвращается сама функция, а не результаты выполнения этой функции.  
  
## Свойства  
 [0...  
          Свойства "n"](../../javascript/reference/0-dot-dot-dot-n-properties-arguments-javascript.md) &#124;[Свойство arguments](../../javascript/reference/arguments-property-function-javascript.md) &#124; [Свойство callee](../../javascript/reference/callee-property-arguments-javascript.md) &#124; [Свойство caller](../../javascript/reference/caller-property-function-javascript.md) &#124; [Свойство constructor](../../javascript/reference/constructor-property-object-javascript.md) &#124; [Свойство "length" \(функция\)](../../javascript/reference/length-property-function-javascript.md) &#124; [Свойство prototype](../../javascript/reference/prototype-property-object-javascript.md)  
  
## Методы  
 [Метод apply](../../javascript/reference/apply-method-function-javascript.md) &#124; [Метод bind](../../javascript/reference/bind-method-function-javascript.md) &#124; [Метод call](../../javascript/reference/call-method-function-javascript.md) &#124; [Метод toString](../../javascript/reference/tostring-method-object-javascript.md) &#124; [Метод valueOf](../../javascript/reference/valueof-method-object-javascript.md)  
  
## Требования  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## См. также  
 [Оператор function](../../javascript/reference/function-statement-javascript.md)   
 [Оператор new](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Оператор var](../../javascript/reference/var-statement-javascript.md)