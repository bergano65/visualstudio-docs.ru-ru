---
title: "Метод concat (массив) (JavaScript) | Microsoft Docs"
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
  - "concat"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "concat - метод (массив)"
  - "Concat - метод"
ms.assetid: bc2b4a6a-209e-4d59-8c24-59db01d53b1e
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Метод concat (массив) (JavaScript)
Объединяет два или более массивов.  
  
## Синтаксис  
  
```  
  
array1.concat([item1[, item2[, . . . [, itemN]]]])   
```  
  
## Параметры  
 `array1`  
 Обязательный.  Объект `Array`, к которому присоединяются другие массивы.  
  
 `item1,. . ., itemN`  
 Необязательный.  Дополнительные элементы, добавляемые в конец массива `array1`.  
  
## Заметки  
 Метод `concat` возвращает объект `Array`, содержащий объединение массива `array1` с любыми другими указанными элементами.  
  
 Добавляемые в массив элементы \(*item1 itemN*\) добавляются, начиная с первого элемента в списке.  Если одни из элементов является массивом, его содержимое добавляется в конец массива `array1`.  Если элемент не является массивом, он добавляется в конец массива как отдельный элемент массива.  
  
 Элементы исходных массивов копируются в результирующий массив в соответствии с указанными ниже правилами.  
  
-   Если объект копируется из одного из объединяемых массивов в новый объект, то ссылка продолжает указывать на тот же объект.  Изменение в новом или исходном массиве приводит к изменению в другом массиве.  
  
-   При добавлении в новый массив строкового или числового значения выполняется только копирование значения.  Изменения значения в одном массиве не влияет на значение в другом.  
  
## Пример  
 В следующем примере показано, как использовать метод `concat` применительно к массиву:  
  
```javascript  
var a, b, c, d;  
a = new Array(1,2,3);  
b = "dog";  
c = new Array(42, "cat");  
d = a.concat(b, c);  
document.write(d);  
  
//Output:   
1, 2, 3, "dog", 42, "cat"  
  
```  
  
## Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## См. также  
 [Метод concat \(строка\)](../../javascript/reference/concat-method-string-javascript.md)   
 [Метод join \(Array\)](../../javascript/reference/join-method-array-javascript.md)