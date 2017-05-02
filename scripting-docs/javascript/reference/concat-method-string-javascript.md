---
title: "Метод concat (строка) (JavaScript) | Microsoft Docs"
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
  - "concat - метод (строка)"
  - "Concat - метод"
ms.assetid: 5d28ebb2-d534-4179-9297-a4c821ee9f24
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Метод concat (строка) (JavaScript)
Возвращает строку, содержащую результат объединения двух или более строк.  
  
## Синтаксис  
  
```  
  
string1. concat([string2[, string3[, . . . [, stringN]]]])  
```  
  
## Параметры  
 `string1`  
 Обязательный.  Объект `String` или строковый литерал, к которому присоединяются все остальные указанные строки.  
  
 `string2,. . ., stringN`  
 Необязательный.  Строка, которую нужно добавить в конец `string1`.  
  
## Заметки  
 Результат вызова метода `concat` эквивалентен операции `result` \= `string1` \+ `string2` \+ `string3` \+ `stringN`.  Изменение значения в исходной или результирующей строке не влияет на значения в других строках.  Если какие\-либо аргументы не являются строками, то перед объединением с `string1` они преобразуются в строки.  
  
## Пример  
 В следующем примере показано использование метода `concat` со строкой.  
  
```javascript  
var str1 = "ABCD"  
var str2 = "EFGH";  
var str3 = "1234";  
var str4 = "5678";  
document.write(str1.concat(str2, str3, str4));  
  
// Output: "ABCDEFGH12345678"  
  
```  
  
## Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Относится к**: [Объект String](../../javascript/reference/string-object-javascript.md)  
  
## См. также  
 [Оператор сложения \(\+\)](../../javascript/reference/addition-operator-decrement-javascript.md)