---
title: "Метод setDate (Date) (JavaScript) | Microsoft Docs"
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
  - "setDate"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "setDate - метод"
  - "даты, установка"
ms.assetid: a84b9b01-a6d0-489f-8a13-e7af9e9630b2
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Метод setDate (Date) (JavaScript)
Задает числовое значение дня месяца объекта доли `Date`, используя локальное время.  
  
## Синтаксис  
  
```  
  
dateObj.setDate(numDate)   
```  
  
## Параметры  
 `dateObj`  
 Обязательный.  Любой объект `Date`.  
  
 `numDate`  
 Обязательный.  Числовое значение, обозначающее день месяца.  
  
## Заметки  
 Задать значение дня месяца с помощью универсалию доли координировал времени в формате UTC, используется метод `setUTCDate`.  
  
 Если значение `numDate` превышает число дней в месяце, то дата свертывает переключается на более поздние месяца и года.  Например, если хранимая дата 5\-ое января 1996. и `setDate(32)` вызываются, дата изменения 1\-ое февраля 1996.  Если `numDate` отрицательное число, то даты откатит к более ранним месяца и года.  Например, если хранимая дата 5\-ое января 1996. и `setDate(-32)` вызываются, дата изменения 29\-ое ноября 1995.  
  
 [Метод setFullYear \(Date\)](../../javascript/reference/setfullyear-method-date-javascript.md) можно использовать для установки год, месяц и день месяца.  
  
## Пример  
 В следующем примере показано, как использовать метод `setDate`.  
  
```javascript  
var date = new Date("12/15/1990");  
date.setDate(30);  
document.write(date);  
  
// Output (for the PST time zone): Sun Dec 30 00:00:00 PST 1990  
  
```  
  
## Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Applies To**: [Объект Date](../../javascript/reference/date-object-javascript.md)  
  
## См. также  
 [Метод getDate \(Date\)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Метод setFullYear \(Date\)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [Метод setMonth \(Date\)](../../javascript/reference/setmonth-method-date-javascript.md)   
 [Метод setUTCDate \(Date\)](../../javascript/reference/setutcdate-method-date-javascript.md)