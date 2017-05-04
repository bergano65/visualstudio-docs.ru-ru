---
title: "Метод indexOf (массив) (JavaScript) | Microsoft Docs"
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
  - "массивы [JavaScript], indexOf - метод"
  - "indexOf - метод [JavaScript]"
ms.assetid: 5bee31ae-aaf1-4466-8cfd-ed287e3cdf17
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Метод indexOf (массив) (JavaScript)
Возвращает индекс первого вхождения значения в массиве.  
  
## Синтаксис  
  
```  
  
array1.indexOf(searchElement[, fromIndex])  
```  
  
#### Параметры  
  
|Параметр|Определение|  
|--------------|-----------------|  
|`array1`|Обязательный.  Объект массива.|  
|`searchElement`|Обязательный.  Значение, которое требуется найти в `array1`.|  
|`fromIndex`|Необязательный.  Индекс массива, с которого начинается поиск.  Если параметр `fromIndex` опущен, то поиск начинается с индекса 0.|  
  
## Возвращаемое значение  
 Индекс первого вхождения `searchElement` в массиве или \-1, если `searchElement` не найден.  
  
## Заметки  
 Метод `indexOf` ищет в массиве указанное значение.  Метод возвращает индекс первого вхождения или \-1, если указанное значение не найдено.  
  
 Поиск выполняется в порядке возрастания индекса.  
  
 Элементы массива сравниваются со значением `searchElement` на предмет строгого равенства, аналогично оператору `===`.  Дополнительные сведения см. в разделе [Операторы сравнения](../../javascript/reference/comparison-operators-javascript.md).  
  
 Необязательный аргумент `fromIndex` указывает индекс массива, с которого начинается поиск.  Если значение параметра `fromIndex` больше или равно длине массива, возвращается \-1.  Если `fromIndex` имеет отрицательное значение, то поиск начинается с индекса, равного длине массива плюс `fromIndex`.  
  
## Пример  
 В следующих примерах показано использование метода `indexOf`.  
  
```javascript  
// Create an array. (The elements start at index 0.)  
var ar = ["ab", "cd", "ef", "ab", "cd"];  
  
// Determine the first location of "cd".  
document.write(ar.indexOf("cd") + "<br/>");  
  
// Output: 1  
  
// Find "cd" starting at index 2.  
document.write(ar.indexOf("cd", 2) + "<br/>");  
  
// Output: 4  
  
// Find "gh" (which is not found).  
document.write (ar.indexOf("gh")+ "<br/>");  
  
// Output: -1  
  
// Find "ab" with a fromIndex argument of -2.  
// The search starts at index 3, which is the array length plus -2.  
document.write (ar.indexOf("ab", -2) + "<br/>");  
// Output: 3  
  
```  
  
## Требования  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## См. также  
 [Методы JavaScript](../../javascript/reference/javascript-methods.md)   
 [Объект Array](../../javascript/reference/array-object-javascript.md)   
 [Использование массивов](../../javascript/advanced/using-arrays-javascript.md)