---
title: "Оператор const (JavaScript) | Microsoft Docs"
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
  - "const_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "объявление переменных, оператор const"
  - "const - оператор"
ms.assetid: 3ad0840f-437f-4163-9571-86ecc5ddb987
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Оператор const (JavaScript)
Объявляет видимую в пределах блока переменную с постоянным значением.  
  
## Синтаксис  
  
```  
const constant1 = value1  
```  
  
#### Параметры  
 `constant1`  
 Имя объявляемой переменной.  
  
 `value1`  
 Исходное значение, присваиваемое переменной.  
  
## Заметки  
 Использование оператора `const` для объявления переменной с постоянным значением, область действия ограничивается в блок, в котором он объявлен.  Значение переменной невозможно изменить.  
  
 Переменная, объявленная с использованием ключевого слова `const`, должна быть инициализирована при объявлении.  
  
## Пример  
 В следующем примере показано использование оператора `const`.  
  
```javascript  
var c = 10;  
{  
    const c = 2;  
   // At this point, c = 2.  
}  
// At this point, c = 10.  
  
// Additional ways to declare a variable using const.  
const name = "Thomas Jefferson";  
const answer = 42, numpages = 10;  
const myarray = new Array();  
  
```  
  
## Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## См. также  
 [Оператор let](../../javascript/reference/let-statement-javascript.md)   
 [Оператор new](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Объект Array](../../javascript/reference/array-object-javascript.md)   
 [Переменные](../../javascript/variables-javascript.md)