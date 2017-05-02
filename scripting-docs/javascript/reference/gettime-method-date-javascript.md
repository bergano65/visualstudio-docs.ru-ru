---
title: "Метод getTime (Date) (JavaScript) | Microsoft Docs"
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
  - "getTime"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "GetTime - метод"
  - "time - метод"
ms.assetid: f0da1d4e-337c-497d-9205-093defbc6d3d
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Метод getTime (Date) (JavaScript)
Получает значение времени в миллисекундах.  
  
## Синтаксис  
  
```  
  
dateObj.getTime()   
```  
  
#### Параметры  
 Обязательная ссылка `dateObj` — это объект `Date`.  
  
## Возвращаемое значение  
 Возвращает количество миллисекунд, истекших с полуночи 1 января 1970 г. до значения времени, сохраненного в объекте `Date`.  Диапазон дат равен приблизительно 285 616 лет в обе стороны от полуночи 1 января 1970 г.  Отрицательные числа указывают даты до 1970 года.  
  
## Заметки  
 При выполнении вычислений с несколькими значениями даты и времени часто бывает полезно определить переменные, равные количеству миллисекунд, содержащихся в дне, часе или минуте.  Примеры.  
  
```javascript  
var minute = 1000 * 60;  
var hour = minute * 60;  
var day = hour * 24;  
```  
  
 Дополнительные сведения об использовании метода`getTime` см. в разделе [Вычисление даты и времени \(JavaScript\)](../../javascript/calculating-dates-and-times-javascript.md).  
  
## Пример  
 В следующем примере показано использование метода `getTime`.  
  
```javascript  
var minute = 1000 * 60;  
var hour = minute * 60;  
var day = hour * 24;  
  
date = new Date("1/1/2001");  
var time = date.getTime();  
  
document.write(Math.round(time / day) + " days from 1/1/1970 to 1/1/2001");  
  
// Output: 11323 days from 1/1/1970 to 1/1/2001  
  
```  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Относится к**: [Объект Date](../../javascript/reference/date-object-javascript.md)  
  
## См. также  
 [Метод setTime \(Date\)](../../javascript/reference/settime-method-date-javascript.md)