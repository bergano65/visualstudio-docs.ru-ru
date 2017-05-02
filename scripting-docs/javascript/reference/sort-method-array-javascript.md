---
title: "Метод sort (Array) (JavaScript) | Microsoft Docs"
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
  - "sort"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Sort - метод"
ms.assetid: 9bd8b54a-c838-4806-85c8-62eebe6bc48c
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Метод sort (Array) (JavaScript)
Сортирует `Array`.  
  
## Синтаксис  
  
```  
  
arrayobj.sort(sortFunction)   
```  
  
## Параметры  
 `arrayObj`  
 Обязательный параметр.  Любой объект `Array`.  
  
 `sortFunction`  
 Необязательный параметр.  Имя функции, применяемой для определения порядка элементов.  Если этот аргумент опущен, элементы сортируются по возрастанию в порядке сортировки символов ASCII.  
  
## Возвращаемое значение  
 Сортируемый массив.  
  
## Заметки  
 Метод `sort` сортирует имеющийся объект `Array`; нового объекта `Array` не создается.  
  
 Если указать функцию в аргументе `sortFunction`, она должна возвращать одно из следующих значений:  
  
-   Отрицательное значение, если первый переданный аргумент меньше второго аргумента.  
  
-   Нуль, если аргументы эквивалентны.  
  
-   Положительное значение, если первый аргумент больше второго аргумента.  
  
## Пример  
 В следующем примере показано, как использовать метод `sort`.  
  
```javascript  
var a = new Array(4, 11, 2, 10, 3, 1);  
  
var b = a.sort();  
document.write(b);  
document.write("<br/>");  
  
// This is ASCII character order.  
// Output: 1,10,11,2,3,4)  
  
// Sort the array elements with a function that compares array elements.  
b = a.sort(CompareForSort);  
document.write(b);  
document.write("<br/>");  
// Output: 1,2,3,4,10,11.  
  
// Sorts array elements in ascending order numerically.  
function CompareForSort(first, second)  
{  
    if (first == second)  
        return 0;  
    if (first < second)  
        return -1;  
    else  
        return 1;   
}  
```  
  
## Требования  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]