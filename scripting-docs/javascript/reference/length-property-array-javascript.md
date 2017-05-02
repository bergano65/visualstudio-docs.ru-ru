---
title: "Свойство length (массив) (JavaScript) | Microsoft Docs"
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
  - "length Property"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Array - объект"
  - "Length - свойство"
  - "length - свойство (массив)"
ms.assetid: e1c6377c-2e84-440a-9660-f1f512e4a938
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Свойство length (массив) (JavaScript)
Получает или задает длину массива.  Представляет собой число, на единицу превышающее индекс последнего определенного элемента массива.  
  
## Синтаксис  
  
```  
  
numVar = arrayObj.length   
```  
  
## Параметры  
 `numVar`  
 Обязательный.  Любое число.  
  
 `arrayObj`  
 Обязательный.  Любой объект `Array`.  
  
## Заметки  
 Массивы JavaScript являются разреженными, а элементы в них не обязательно должны следовать подряд.  Свойство `length` не обязательно совпадает с числом элементов массива.  Например, в следующем определении массива свойство `my_array.length` содержит значение 7, а не 2:  
  
```javascript  
var my_array = new Array( );  
my_array[0] = "Test";  
my_array[6] = "Another Test";  
```  
  
 Если свойство `length` получает значение, меньшее его предыдущего значения, массив усекается, а все элементы, индексы которых равны или больше нового значения свойства `length`, теряются.  
  
 Если свойство length получает значение, большее его предыдущего значения, массив расширяется, а все новые созданные элементы имеют значение `undefined`.  
  
 В следующем примере показано применение свойства `length`.  
  
```javascript  
var a;  
a = new Array(0,1,2,3,4);  
document.write(a.length);  
  
// Output  
// 5  
  
```  
  
## Требования  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
> [!NOTE]
>  Начиная с Internet Explorer 9 \(стандартный режим\), конечные запятые, включаемые в инициализацию массива, обрабатываются иначе.