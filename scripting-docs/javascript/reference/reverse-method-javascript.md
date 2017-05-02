---
title: "Метод reverse (JavaScript) | Microsoft Docs"
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
  - "reverse"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "массивы [Visual Studio], расположение элементов в обратном порядке"
  - "reverse - метод"
  - "обращение порядка элементов"
ms.assetid: 02ab051b-79b8-4646-b502-381671e78c12
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Метод reverse (JavaScript)
Изменяет порядок элементов в `Array` на обратный.  
  
## Синтаксис  
  
```  
  
arrayObj.reverse()   
```  
  
## Параметры  
 `arrayObj`  
 Обязательный параметр.  Любой объект `Array`.  
  
## Возвращаемое значение  
 Обращенный массив.  
  
## Заметки  
 Требуемая ссылка на `arrayObj` — объект `Array`.  
  
 Метод `reverse` размещает элементы объекта `Array` в обратном порядке.  При выполнении этого метода новый объект `Array` не создается.  
  
 Если массив не является непрерывен, метод `reverse` создает элементы в массиве, которые заполняют пробелы в нем.  Каждый из этих созданных элементов имеет значение `undefined`.  
  
## Пример  
 В следующем примере показано использование метода `reverse`.  
  
```javascript  
var arr = new Array(0,1,2,3,4);   
var reverseArr = arr.reverse();  
document.write(reverseArr);  
  
// Output:  
// 4,3,2,1,0  
  
```  
  
## Требования  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## См. также  
 [Метод concat \(массив\)](../../javascript/reference/concat-method-array-javascript.md)