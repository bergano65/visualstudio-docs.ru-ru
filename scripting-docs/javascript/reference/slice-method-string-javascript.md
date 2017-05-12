---
title: "Метод slice (String) (JavaScript) | Microsoft Docs"
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
  - "slice"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "slice - метод"
  - "строки [Visual Studio], возврат символов"
ms.assetid: 80cd77a6-3718-492e-8e96-f909d8721d91
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Метод slice (String) (JavaScript)
Возвращает фрагмент строки.  
  
## Синтаксис  
  
```  
  
stringObj.slice(start, [end])   
```  
  
## Параметры  
 `stringObj`  
 Обязательный параметр.  Объект `String` или строковый литерал.  
  
 `start`  
 Обязательный параметр.  Индекс начала указанного фрагмента `stringObj`.  
  
 `end`  
 Необязательный параметр.  Индекс конца указанного фрагмента `stringObj`.  Подстрока включает знаки до знака, задаваемого значением `end`, но не включая его.  Если это значение не указывается, подстрока заканчивается в конце `stringObj`.  
  
## Заметки  
 Метод `slice` возвращает объект `String`, который содержит указанный фрагмент `stringObj`.  
  
 Метод `slice` осуществляет копирование фрагмента вплоть до символа, указанного в `end` \(не включая его\).  
  
 Если значение `start` является отрицательным, оно обрабатывается в соответствии с выражением *length* \+ `start`, где *length* — длина строки.  Если значение `end` отрицательно, оно рассматривается как *length* \+ `end`.  Если `end` не задано, то копирование происходит до конца `stringObj`.  Если значение `end` меньше `start`, знаки в новую строку не копируются.  
  
## Пример  
 В первом примере метод `slice` возвращает всю строку.  Во втором примере метод `slice` возвращает всю строку, за исключением последнего символа.  
  
```javascript  
var str1 = "all good boys do fine";  
  
var slice1 = str1.slice(0);  
var slice2 = str1.slice(0,-1);  
var slice3 = str1.slice(4);  
var slice4 = str1.slice(4, 8);  
  
document.write(slice1 + "<br/>");  
document.write(slice2 + "<br/>");  
document.write(slice3 + "<br/>");  
document.write(slice4);  
  
// Output:  
// all good boys do fine  
// all good boys do fin  
// good boys do fine  
// good  
  
```  
  
## Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Применение**: [Объект String](../../javascript/reference/string-object-javascript.md)  
  
## См. также  
 [Метод slice \(массив\)](../../javascript/reference/slice-method-array-javascript.md)