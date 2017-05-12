---
title: "Оператор let (JavaScript) | Microsoft Docs"
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
  - "let_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "let - оператор"
  - "объявление переменных, оператор let"
ms.assetid: c7e4f8a9-8f54-47b6-aed2-956959c1ecfd
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Оператор let (JavaScript)
Объявляет видимую в пределах блока переменную.  
  
## Синтаксис  
  
```  
let variable1 = value1  
```  
  
#### Параметры  
 `variable1`  
 Имя объявляемой переменной.  
  
 `value1`  
 Исходное значение, присваиваемое переменной.  
  
## Заметки  
 Использование оператора `let` для объявления переменной, область действия ограничивается в блок, в котором он объявлен.  Значения могут быть присвоены переменным при их объявлении или позже в скрипте.  
  
 Переменную, объявленная с использованием ключевого слова `let`, невозможно использовать до ее объявление; в противном случае возникнет ошибка.  
  
 Если не инициализировать переменную в операторе `let`, ей автоматически присваивается значение [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] `undefined`.  
  
## Пример  
 В следующем примере показано использование оператора `let`.  
  
```javascript  
var  l = 10;  
{  
    let l = 2;  
   // At this point, l = 2.  
}  
// At this point, l = 10.  
  
// Additional ways to declare a variable using let.  
let index;  
let name = "Thomas Jefferson";  
let answer = 42, counter, numpages = 10;  
let myarray = new Array();  
  
```  
  
## Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## См. также  
 [Оператор const](../../javascript/reference/const-statement-javascript.md)   
 [Оператор new](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Объект Array](../../javascript/reference/array-object-javascript.md)   
 [Переменные](../../javascript/variables-javascript.md)