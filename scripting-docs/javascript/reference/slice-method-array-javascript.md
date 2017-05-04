---
title: "Метод slice (Array) (JavaScript) | Microsoft Docs"
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
  - "отсчитываемый от нуля индекс"
  - "Array - объект"
  - "slice - метод"
ms.assetid: 3c122219-14de-4126-b091-809659c026d6
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Метод slice (Array) (JavaScript)
Возвращает фрагмент массива.  
  
## Синтаксис  
  
```  
  
arrayObj.slice(start, [end])   
```  
  
## Параметры  
 `arrayObj`  
 Обязательный.  Объект `Array`.  
  
 `start`  
 Обязательный.  Начало указанного фрагмента `arrayObj`.  
  
 `end`  
 Необязательный.  Конец указанного фрагмента `arrayObj`.  
  
## Заметки  
 Метод `slice` возвращает объект `Array`, содержащий указанный фрагмент `arrayObj`.  
  
 Метод `slice` осуществляет копирование вплоть до элемента, указанного параметром `end` \(исключительно\).  Если значение `start` отрицательное, оно обрабатывается как `length` \+ `start`, где `length` — длина массива.  Если значение `end` отрицательное, оно обрабатывается как `length` \+ `end`, где `length` — длина массива.  Если параметр `end` не указан, извлечение продолжается до конца `arrayObj`.  Если `end` находится до `start`, в новый массив не копируется ни одного элемента.  
  
## Пример  
 В следующих примерах показано использование метода `slice`.  В первом примере все элементы `myArray`, кроме последнего, копируются в `newArray`.  Во втором примере только последние два элемента `myArray` копируются в `newArray`.  
  
```javascript  
var origArray = [3, 5, 7, 9];  
var newArray = origArray. slice(0, -1);  
document.write(origArray);  
document.write("<br/>");  
newArray = origArray. slice(-2);  
document.write(newArray);  
  
// Output:  
// 3,5,7,9  
// 7,9  
  
```  
  
## Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## См. также  
 [Метод slice \(строка\)](../../javascript/reference/slice-method-string-javascript.md)   
 [Объект String](../../javascript/reference/string-object-javascript.md)