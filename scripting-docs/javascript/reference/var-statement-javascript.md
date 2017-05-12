---
title: "Оператор var (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/22/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "var_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "объявление переменных, оператор var"
  - "var - оператор"
ms.assetid: 56f900af-a5c4-4667-9664-5956d30f0aae
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Оператор var (JavaScript)
Объявляет переменную  
  
## Синтаксис  
  
```  
var variable1 = value1  
```  
  
## Параметры  
 `variable1`  
 Объявленное имя переменной.  
  
 `value1`  
 Исходное значение, присваиваемое переменной.  
  
## Заметки  
 Используйте оператор `var` для объявления переменных.  Значения могут быть присвоены переменным при их объявлении или позже в скрипте.  
  
 Переменная, объявленная в первый раз, появляется в скрипте.  
  
 Можно объявить переменную без ключевого слова `var` и присвоить ей значение.  Это называется *неявным объявлением*, применять его не рекомендуется.  Неявное объявление дает переменной глобальную область видимости.  При объявлении переменной на уровне процедуры обычно не требуется, чтобы эта переменная обладала глобальной областью видимости.  Чтобы переменная не обладала глобальной областью видимости, необходимо использовать ключевое слово `var` в объявлении переменной.  
  
 Если не инициализировать переменную в операторе `var`, ей автоматически присваивается значение [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] `undefined`.  
  
## Пример  
 В следующих примерах показано использование оператора `var`.  
  
```javascript  
var index;  
var name = "Thomas Jefferson";  
var answer = 42, counter, numpages = 10;  
var myarray = new Array();  
```  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## См. также  
 [Оператор function](../../javascript/reference/function-statement-javascript.md)   
 [Оператор new](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Объект Array](../../javascript/reference/array-object-javascript.md)   
 [Переменные](../../javascript/variables-javascript.md)