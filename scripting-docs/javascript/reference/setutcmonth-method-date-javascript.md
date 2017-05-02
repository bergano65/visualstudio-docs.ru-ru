---
title: "Метод setUTCMonth (Date) (JavaScript) | Microsoft Docs"
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
  - "setUTCMonth"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "даты, время в формате UTC"
  - "Month - метод"
  - "setUTCMonth - метод"
  - "даты в формате UTC, параметр"
ms.assetid: cdac5f64-c4fd-44cc-ba3a-9a8dd3dd3fad
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Метод setUTCMonth (Date) (JavaScript)
Устанавливает значение месяца в объекте `Date`, используя универсальное время UTC.  
  
## Синтаксис  
  
```  
  
dateObj.setUTCMonth(numMonth[, dateVal])   
```  
  
## Параметры  
 `dateObj`  
 Обязательный.  Любой объект `Date`.  
  
 `numMonth`  
 Обязательный.  Числовое значение, равное месяцу.  Значение для января равно 0, значения других месяцев увеличиваются соответственно.  
  
 `dateVal`  
 Необязательный.  Числовое значение, представляющее день месяца.  Если этот аргумент не указан, используется значение из вызова метода `getUTCDate`.  
  
## Заметки  
 Чтобы задать значение месяца с помощью местного времени, используйте метод `setMonth`.  
  
 Если значение аргумента `numMonth` превышает 11 \(январь соответствует месяцу 0\) или является отрицательным числом, хранящееся значение года увеличивается или уменьшается соответствующим образом.  Например, если сохранена дата "5 января 1996 г. 00:00:00,00" и вызывается метод **setUTCMonth\(14\)**, дата принимает значение "5 марта 1997 г. 00:00:00,00".  
  
 С помощью метода **setUTCFullYear** можно задать год, месяц и день месяца.  
  
## Пример  
 В следующем примере показано использование метода `setUTCMonth`.  
  
```javascript  
function SetUTCMonthDemo(newmonth){  
   var d, s;                       // Declare variables.  
   d = new Date();                 // Create Date object.  
   d.setUTCMonth(newmonth);        // Set UTC month.  
   s = "Current setting is ";  
   s += d.toUTCString();   
   return(s);                      // Return new setting.  
}  
```  
  
## Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Относится к**: [Объект Date](../../javascript/reference/date-object-javascript.md)  
  
## См. также  
 [Метод getMonth \(Date\)](../../javascript/reference/getmonth-method-date-javascript.md)   
 [Метод getUTCMonth \(Date\)](../../javascript/reference/getutcmonth-method-date-javascript.md)   
 [Метод setMonth \(Date\)](../../javascript/reference/setmonth-method-date-javascript.md)