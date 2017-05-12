---
title: "Метод toString (Array) | Microsoft Docs"
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
ms.assetid: 71fbea85-3e00-41b0-b167-25e4281e5e8a
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Метод toString (Array)
Возвращает строковое представление массива.  
  
## Синтаксис  
  
```  
  
array.toString()  
```  
  
## Параметры  
 `array`  
 Обязательный.  Массив, который необходимо представить в виде строки.  
  
## Возвращаемое значение  
 Строковое представление массива.  
  
## Заметки  
 Элементы объекта `Array` преобразуются в строки.  Результирующие строки объединяются и разделяются запятыми.  
  
## Пример  
 В следующем примере показано использование метода **toString** с массивом.  
  
```javascript  
var arr = [1, 2, 3, 4];  
var s = arr.toString();  
document.write(s);  
  
// Output: 1,2,3,4  
  
```  
  
## Требования  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]