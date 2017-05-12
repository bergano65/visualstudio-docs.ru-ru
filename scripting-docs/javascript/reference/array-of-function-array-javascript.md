---
title: "Функция Array.of (Array) (JavaScript) | Microsoft Docs"
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
ms.assetid: 2884dda3-65d1-4990-9afe-87865c2d4f7f
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Функция Array.of (Array) (JavaScript)
Возвращает массив из переданных аргументов.  
  
## Синтаксис  
  
```  
Array.of(element0[, element1][, ...][,elementN]);  
```  
  
#### Параметры  
 `element0,...,elementN`  
 Необязательный.  Элементы, которые нужно поместить в массив.  Создает массив с числом элементов n \+ 1 и значением length, равным n \+ 1.  
  
## Заметки  
 Эта функция работает как вызов `new Array(args)`, однако `Array.of` не определяет особое поведение в случае передачи одного аргумента.  
  
## Пример  
 В следующем примере создается массив из переданных чисел.  
  
```javascript  
var arr = Array.of(1, 2, 3);  
// arr[0] == 1  
  
```  
  
## Пример  
 В следующем примере показано различие между использованием `Array.of` и `new Array`.  
  
```javascript  
var arr1 = Array.of(3);  
// arr1[0] == 3  
  
// With new Array, a single argument specifies  
// the length of the new array.  
var arr2 = new Array(3);  
// arr2[0] is undefined  
// arr2.length == 3  
  
```  
  
## Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]