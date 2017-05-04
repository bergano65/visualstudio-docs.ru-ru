---
title: "Метод setFullYear (Date) (JavaScript) | Microsoft Docs"
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
  - "setFullYear"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Year - метод"
  - "setFullYear - метод"
  - "даты, установка"
ms.assetid: 635e4f5a-0210-4c01-8152-b0da4146f6ff
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Метод setFullYear (Date) (JavaScript)
Устанавливает значение года объекта `Date`, используя локальное время.  
  
## Синтаксис  
  
```  
  
dateObj.setFullYear(numYear[, numMonth[, numDate]])   
```  
  
## Параметры  
 `dateObj`  
 Обязательный.  Любой объект `Date`.  
  
 `numYear`  
 Обязательный.  Числовое значение в год.  
  
 `numMonth`  
 Необязательный.  Числовое значение нулевой\-, основанное на месяц \(0 11\-ое января на декабрь\).  Обязательно указывать, если `numDate` указано.  
  
 `numDate`  
 Необязательный.  Числовое значение, равное в день месяца.  
  
## Заметки  
 Все методы **set**, принимающие необязательные аргументы, в случае, когда такой аргумент не задан, используют значение, возвращенное соответствующим методом **get**.  Например, если аргумент `numMonth` является необязательным, но не определен, используйте [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] значение, возвращаемое из метода **getMonth**.  
  
 Кроме того, если значение аргумента больше, чем его диапазона календаря или отрицательное, то даты накаты или назад в качестве подходящего.  
  
 Установка год с помощью универсалию координировал времени в формате UTC, используется метод `setUTCFullYear`.  
  
 Диапазон лет, поддерживаемых в объекте date приблизительно 285.616 лет до и после 1970.  
  
## Пример  
 В следующем примере показано использование метода `setFullYear`.  
  
```javascript  
var date1 = new Date("1/1/2001");  
date1.setFullYear(2007);  
  
var date2 = new Date("1/1/2001");  
date2.setFullYear(2008, 10, 3);   
  
document.write (date1.toLocaleString());  
document.write ("<br />");  
document.write (date2.toLocaleString());  
  
// Output:  
// Monday, January 01, 2007 12:00:00 AM  
// Monday, November 03, 2008 12:00:00 AM  
  
```  
  
## Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Applies To**: [Объект Date](../../javascript/reference/date-object-javascript.md)  
  
## См. также  
 [Метод getFullYear \(Date\)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [Метод getUTCFullYear \(Date\)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [Метод setUTCFullYear \(Date\)](../../javascript/reference/setutcfullyear-method-date-javascript.md)