---
title: "Метод setUTCMinutes (Date) (JavaScript) | Microsoft Docs"
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
  - "setUTCMinutes"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "даты, время в формате UTC"
  - "минуты"
  - "setUTCMinutes - метод"
  - "время в формате UTC, параметр"
ms.assetid: 2415e788-6d28-46dd-a103-0931a1fd1446
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Метод setUTCMinutes (Date) (JavaScript)
Задает значение минут в объекте `Date`, используя время в формате UTC.  
  
## Синтаксис  
  
```  
  
dateObj.setUTCMinutes(numMinutes[, numSeconds[, numMilli]])   
```  
  
## Параметры  
 `dateObj`  
 Обязательный.  Любой объект `Date`.  
  
 `numMinutes`  
 Обязательный.  Числовое значение, равное количеству минут.  Должен указываться, если используется какой\-либо из следующих аргументов.  
  
 *numSeconds*  
 Необязательный.  Числовое значение, равное количеству секунд.  Должен указываться, если используется `numMilli`.  
  
 `numMilli`  
 Необязательный.  Числовое значение, равное количеству миллисекунд.  
  
## Заметки  
 Все методы **set**, принимающие необязательные аргументы, в случае, когда необязательный аргумент не задан, используют значение, возвращаемое соответствующими методами **get**.  Например, если аргумент *numSeconds* не задан, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] использует значение, возвращаемое методом `getUTCSeconds`.  
  
 Для изменения значения минут с использованием местного времени используется метод `setMinutes`.  
  
 Если значение аргумента превышает верхнюю границу его диапазона или является отрицательным числом, остальные хранящиеся значения изменяются соответственно.  Например, если сохранена дата "00:00:00.00 5 января 1996 г." и вызывается метод **setUTCMinutes\(70\)**, дата принимает значение "01:10:00.00 5 января 1996 г.".  
  
 С помощью метода **setUTCHours** можно задать часы, минуты, секунды и миллисекунды.  
  
## Пример  
 В следующем примере показано использование метода `setUTCMinutes`.  
  
```javascript  
function SetUTCMinutesDemo(nmin, nsec){  
   var d, s;                    // Declare variables.  
   d = new Date();              // Create Date object.  
   d.setUTCMinutes(nmin,nsec);  // Set UTC minutes.  
   s = "Current setting is " + d.toUTCString()   
   return(s);                   // Return new setting.  
}  
```  
  
## Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Относится к**: [Объект Date](../../javascript/reference/date-object-javascript.md)  
  
## См. также  
 [Метод getMinutes \(Date\)](../../javascript/reference/getminutes-method-date-javascript.md)   
 [Метод getUTCMinutes \(Date\)](../../javascript/reference/getutcminutes-method-date-javascript.md)   
 [Метод setMinutes \(Date\)](../../javascript/reference/setminutes-method-date-javascript.md)