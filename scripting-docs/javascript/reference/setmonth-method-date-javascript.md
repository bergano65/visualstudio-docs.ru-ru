---
title: "Метод setMonth (Date) (JavaScript) | Microsoft Docs"
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
  - "setMonth"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Month - метод"
  - "setMonth - метод"
ms.assetid: 4f5be295-d536-46c0-b3a4-ad06457efe82
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Метод setMonth (Date) (JavaScript)
Устанавливает значение месяца в объекте `Date`, используя локальное время.  
  
## Синтаксис  
  
```  
  
dateObj. setMonth(numMonth[, dateVal])   
```  
  
## Параметры  
 `dateObj`  
 Обязательный.  Любой объект `Date`.  
  
 `numMonth`  
 Обязательный.  Числовое значение, равное месяцу.  Значение для января равно 0, значения других месяцев увеличиваются соответственно.  
  
 `dateVal`  
 Необязательный.  Числовое значение, представляющее день месяца.  Если это значение не предоставлено, используется значение из вызова метода `getDate`.  
  
## Заметки  
 Чтобы установить значение месяца с использованием универсального времени \(UTC\), используйте метод `setUTCMonth`.  
  
 Если значение `numMonth` превышает 11 \(январь соответствует месяцу 0\) или является отрицательным числом, хранящееся значение года изменяется соответствующим образом.  Например, если сохранена дата "5 января 1996 г." и вызывается метод **setMonth\(14\)**, дата принимает значение "5 марта 1997 г.".  
  
 С помощью метода **setFullYear** можно задать год, месяц и день месяца.  
  
## Пример  
 В следующем примере показано использование метода `setMonth`.  
  
```javascript  
date = new Date('1/1/1990');  
date.setMonth(14);  
document.write(date);  
  
// Output: Fri Mar 1 00:00:00 PST 1991  
// Note that the time zone corresponds to the time zone on the local computer.  
  
```  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Относится к**: [Объект Date](../../javascript/reference/date-object-javascript.md)  
  
## См. также  
 [Метод getMonth \(Date\)](../../javascript/reference/getmonth-method-date-javascript.md)   
 [Метод getUTCMonth \(Date\)](../../javascript/reference/getutcmonth-method-date-javascript.md)   
 [Метод setUTCMonth \(Date\)](../../javascript/reference/setutcmonth-method-date-javascript.md)