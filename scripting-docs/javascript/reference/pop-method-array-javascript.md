---
title: "Метод pop (Array) (JavaScript) | Microsoft Docs"
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
  - "pop"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Pop - метод"
ms.assetid: 4fae7f98-29f1-4041-ba43-601f2e5145ec
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Метод pop (Array) (JavaScript)
Удаляет последний элемент из массива и возвращает его.  
  
## Синтаксис  
  
```  
  
arrayObj.pop( )  
```  
  
## Заметки  
 Методы [push](../../javascript/reference/push-method-array-javascript.md) и `pop` позволяют смоделировать стек, в котором для хранения данных используется принцип "последним поступил — первым обслужен" \(LIFO\).  
  
 Обязательная ссылка `arrayObj` — это объект `Array`.  
  
 Если массив пуст, возвращается значение `undefined`.  
  
## Пример  
 В следующем примере показано использование метода `pop`.  
  
```javascript  
var number;  
var my_array = new Array();  
  
my_array.push (5, 6, 7);  
my_array.push (8, 9);  
  
number = my_array.pop();  
while (number != undefined)  
   {  
   document.write (number + " ");  
   number = my_array.pop();  
   }  
  
// Output: 9 8 7 6 5  
```  
  
## Требования  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## См. также  
 [Метод push \(Array\)](../../javascript/reference/push-method-array-javascript.md)