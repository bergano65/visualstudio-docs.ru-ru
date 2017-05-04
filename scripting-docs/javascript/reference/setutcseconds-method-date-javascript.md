---
title: "Метод setUTCSeconds (Date) (JavaScript) | Microsoft Docs"
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
  - "setUTCSeconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "даты, время в формате UTC"
  - "seconds - метод"
  - "setUTCSeconds - метод"
  - "время в формате UTC, параметр"
ms.assetid: e035e282-b39d-4d1d-8771-c17542fd6493
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Метод setUTCSeconds (Date) (JavaScript)
Устанавливает значение секунд в объекте `Date`, используя универсальное время UTC.  
  
## Синтаксис  
  
```  
  
dateObj.setUTCSeconds(numSeconds[, numMilli])   
```  
  
## Параметры  
 `dateObj`  
 Обязательный.  Любой объект `Date`.  
  
 *numSeconds*  
 Обязательный.  Числовое значение, равное количеству секунд.  
  
 `numMilli`  
 Необязательный.  Числовое значение, равное количеству миллисекунд.  
  
## Заметки  
 Все методы **set**, принимающие необязательные аргументы, в случае, когда необязательный аргумент не задан, используют значение, возвращаемое соответствующими методами **get**.  Например, если аргумент `numMilli` не задан, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] использует значение, возвращенное методом `getUTCMilliseconds`.  
  
 Чтобы установить значение секунд с использованием местного времени, используйте метод `setSeconds`.  
  
 Если значение аргумента превышает верхнюю границу его диапазона или является отрицательным числом, остальные хранящиеся значения изменяются соответственно.  Например, если сохранена дата "5 января 1996 г., 00:00:00,00" и вызывается метод **setSeconds\(150\)**, дата принимает значение "5 января 1996 г., 00:02:30,00".  
  
 С помощью метода **setUTCHours** можно задать часы, минуты, секунды и миллисекунды.  
  
## Пример  
 В следующем примере показано использование метода `setUTCSeconds`.  
  
```javascript  
function SetUTCSecondsDemo(nsec){  
// Create Date object.  
    var d = new Date();       
// Set UTC seconds.  
    d.setUTCSeconds(nsec);    
    var s = "Current setting is ";  
    s += d.toUTCString();  
// Return new setting.  
    return(s);                
}  
```  
  
## Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Относится к**: [Объект Date](../../javascript/reference/date-object-javascript.md)  
  
## См. также  
 [Метод getSeconds \(Date\)](../../javascript/reference/getseconds-method-date-javascript.md)   
 [Метод getUTCSeconds \(Date\)](../../javascript/reference/getutcseconds-method-date-javascript.md)   
 [Метод setSeconds \(Date\)](../../javascript/reference/setseconds-method-date-javascript.md)