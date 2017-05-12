---
title: "Функция Date.parse (JavaScript) | Microsoft Docs"
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
  - "parse"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date.parse - функция [JavaScript]"
  - "parse - функция [JavaScript]"
ms.assetid: ed737e50-6398-4462-8779-2af3c03f8325
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# Функция Date.parse (JavaScript)
Выполняет синтаксический анализ строки, содержащей дату, и возвращает количество миллисекунд, истекших с полуночи 1 января 1970 г.  
  
## Синтаксис  
  
```  
Date.parse(dateVal)   
```  
  
## Заметки  
 Обязательный аргумент `dateVal` является либо строкой, содержащей дату, либо значением VT\_DATE, извлеченным из объекта ActiveX или другого объекта.  Дополнительные сведения о строках дат, которые может синтаксически проанализировать функция `Date.parse`, см. [Строки даты и времени](../../javascript/date-and-time-strings-javascript.md).  
  
 Функция `Date.parse` возвращает целое значение, представляющее число миллисекунд между 1 января 1970 года и указанной в `dateVal` датой.  
  
## Пример  
 В следующем примере показано, как используется функция `Date.parse`.  
  
```javascript  
var dateString = "November 1, 1997 10:15 AM";  
var mSec = Date.parse(dateString);  
document.write(mSec);  
// Output: 878404500000  
```  
  
## Пример  
 Следующий пример возвращает разницу между предоставленной датой и 01.01.1970.  
  
```javascript  
var minMilli = 1000 * 60;  
var hrMilli = minMilli * 60;  
var dyMilli = hrMilli * 24;  
  
var testDate = new Date("June 1, 1990");  
var ms = Date.parse(testDate);  
var days = Math.round(ms / dyMilli);  
  
var dateStr = "";  
dateStr += "There are " + days + " days ";  
dateStr += "between 01/01/1970 and " + testDate;  
document.write(dateStr);  
  
// Output: There are 7456 days between 01/01/1970 and Fri Jun 1 00:00:00 PDT 1990  
  
```  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## См. также  
 [Метод getDate \(Date\)](../../javascript/reference/getdate-method-date-javascript.md)