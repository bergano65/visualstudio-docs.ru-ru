---
title: "Метод lastIndexOf (массив) (JavaScript) | Microsoft Docs"
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
  - "массивы [JavaScript], lastIndexOf - метод"
  - "lastIndexOf - метод [JavaScript]"
ms.assetid: 04f5145d-007e-498f-b06f-11ab384c2968
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Метод lastIndexOf (массив) (JavaScript)
Возвращает индекс последнего вхождения указанного значения в массиве.  
  
## Синтаксис  
  
```  
  
array1.lastIndexOf(searchElement[, fromIndex])  
```  
  
#### Параметры  
  
|Параметр|Определение|  
|--------------|-----------------|  
|`array1`|Обязательный.  Объект массива, в котором выполняется поиск.|  
|`searchElement`|Обязательный.  Значение, которое требуется найти в `array1`.|  
|`fromIndex`|Необязательный.  Индекс массива, с которого начинается поиск.  Если аргумент `fromIndex` опущен, поиск начинается с последнего индекса в массиве.|  
  
## Возвращаемое значение  
 Индекс последнего вхождения `searchElement` в массиве или \-1, если `searchElement` не найден.  
  
## Заметки  
 Метод `lastIndexOf` ищет в массиве указанное значение.  Метод возвращает индекс первого вхождения или \-1, если указанное значение не найдено.  
  
 Поиск выполняется в порядке убывания индекса \(начиная с последнего элемента\).  Для поиска в порядке возрастания используется метод [Метод indexOf \(массив\)](../../javascript/reference/indexof-method-array-javascript.md).  
  
 Элементы массива сравниваются со значением `searchElement` на предмет строгого равенства, аналогично сравнению с использованием оператора `===`.  Дополнительные сведения см. в разделе [Операторы сравнения](../../javascript/reference/comparison-operators-javascript.md).  
  
 Необязательный аргумент `fromIndex` указывает индекс массива, с которого начинается поиск.  Если `fromIndex` больше или равен длине массива, выполняется поиск во всем массиве.  Если `fromIndex` имеет отрицательное значение, то поиск начинается с индекса, равного длине массива плюс `fromIndex`.  Если вычисленный индекс меньше 0, возвращается \-1.  
  
## Пример  
 В следующих примерах показано использование метода `lastIndexOf`.  
  
```javascript  
// Create an array.  
var ar = ["ab", "cd", "ef", "ab", "cd"];  
  
// Determine the first location, in descending order, of "cd".  
document.write(ar.lastIndexOf("cd") + "<br/>");  
  
// Output: 4  
  
// Find "cd" in descending order, starting at index 2.  
document.write(ar.lastIndexOf("cd", 2) + "<br/>");  
  
// Output: 1  
  
// Search for "gh" (which is not found).  
document.write(ar.lastIndexOf("gh")+ "<br/>");  
  
// Output: -1  
  
// Find "ab" with a fromIndex argument of -3.  
// The search in descending order starts at index 3,  
// which is the array length minus 2.  
document.write(ar.lastIndexOf("ab", -3) + "<br/>");  
// Output: 0  
  
```  
  
## Требования  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## См. также  
 [Метод indexOf \(массив\)](../../javascript/reference/indexof-method-array-javascript.md)   
 [Объект Array](../../javascript/reference/array-object-javascript.md)   
 [Использование массивов](../../javascript/advanced/using-arrays-javascript.md)