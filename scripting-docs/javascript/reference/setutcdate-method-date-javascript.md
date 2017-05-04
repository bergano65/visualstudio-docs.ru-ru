---
title: "Метод setUTCDate (Date) (JavaScript) | Microsoft Docs"
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
  - "setUTCDate"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "даты, параметр"
  - "даты, время в формате UTC"
  - "setUTCDate - метод"
  - "даты в формате UTC, параметр"
ms.assetid: e6c3b876-70fe-4103-b197-6c84c078ce10
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Метод setUTCDate (Date) (JavaScript)
Задает числовое значение дня месяца из объекта `Date`, используя универсальное время UTC.  
  
## Синтаксис  
  
```  
  
dateObj.setUTCDate(numDate)   
```  
  
## Параметры  
 `dateObj`  
 Обязательный.  Любой объект `Date`.  
  
 *numDate*  
 Обязательный.  Числовое значение, обозначающее день месяца.  
  
## Заметки  
 Чтобы задать день месяца с использованием местного времени, используйте метод `setDate`.  
  
 Если значение *numDate* превышает количество дней в месяце, сохраненном в объекте **Date**, или является отрицательным числом, устанавливается дата, равная разности между значением *numDate* и числом дней в сохраненном месяце.  Например, если сохранена дата "5 января 1996 г." и вызывается метод **setUTCDate\(32\)**, то дата изменяется на "1 февраля 1996 г.".  Отрицательные числа ведут себя аналогично.  
  
 С помощью метода **setUTCFullYear** можно задать год, месяц и день месяца.  
  
## Пример  
 В следующем примере показано использование метода `setUTCDate`.  
  
```javascript  
function SetUTCDateDemo(newdayofmonth){  
   var d = new Date();           // Create Date object.  
   d.setUTCDate(newdayofmonth);  // Set UTC day of month.  
   var s = "Current setting is ";  
   s += d.toUTCString();   
   return(s);                    // Return new setting.  
}  
```  
  
## Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Относится к**: [Объект Date](../../javascript/reference/date-object-javascript.md)  
  
## См. также  
 [Метод getDate \(Date\)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Метод getUTCDate \(Date\)](../../javascript/reference/getutcdate-method-date-javascript.md)   
 [Метод setDate \(Date\)](../../javascript/reference/setdate-method-date-javascript.md)