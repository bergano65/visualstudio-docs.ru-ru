---
title: "Оператор delete (JavaScript) | Microsoft Docs"
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
  - "delete_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "элементы массива, удаление"
  - "свойства, удаление"
  - "Оператор delete"
ms.assetid: 55c6487e-96ea-455b-a7ed-dc35c41ac2f3
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Оператор delete (JavaScript)
Удаляет свойство из объекта или элемент из массива.  
  
## Синтаксис  
  
```  
delete expression  
```  
  
## Заметки  
 Аргумент `expression` — допустимое выражение [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], которое обычно дает в результате имя свойства или элемент массива.  
  
 Если результатом `expression` является объект, свойство, указанное в `expression`, существует, и объект не допустит его удаления, то возвращается значение `false`.  
  
 Во всех остальных случаях возвращается значение `true`.  
  
## Пример  
 В следующем примере показано, как удалить элемент из массива.  
  
```javascript  
// Create an array.  
var ar = new Array (10, 11, 12, 13, 14);  
  
// Remove an element from the array.  
delete ar[1];  
  
// Print the results.  
document.write ("element 1: " + ar[1]);  
document.write ("<br />");  
document.write ("array: " + ar);  
// Output:  
//  element 1: undefined  
//  array: 10,,12,13,14  
```  
  
## Пример  
 В следующем примере показано, как удалять свойства из объекта.  
  
```javascript  
// Create an object and add expando properties.  
var myObj = new Object();  
myObj.name = "Fred";  
myObj.count = 42;  
  
// Delete the properties from the object.  
delete myObj.name;  
delete myObj["count"];  
  
// Print the results.  
document.write ("name: " + myObj.name);  
document.write ("<br />");  
document.write ("count: " + myObj.count);  
// Output:  
//  name: undefined  
//  count: undefined  
```  
  
## Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## См. также  
 [Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md)   
 [Сводный список операторов \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)