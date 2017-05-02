---
title: "Метод setMinutes (Date) (JavaScript) | Microsoft Docs"
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
  - "setMinutes"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "минуты"
  - "setMinutes - метод"
ms.assetid: 34c959cd-cd29-4cee-8e04-9061cf6d42f3
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Метод setMinutes (Date) (JavaScript)
Устанавливает значение минут в объекте **Date**, используя локальное время.  
  
## Синтаксис  
  
```  
  
dateObj.setMinutes(numMinutes[, numSeconds[, numMilli]])   
```  
  
## Параметры  
 `dateObj`  
 Обязательный.  Любой объект `Date`.  
  
 `numMinutes`  
 Обязательный.  Числовое значение, равное количеству минут.  Должен указываться, если используется какой\-либо из следующих аргументов.  
  
 *numSeconds*  
 Необязательный.  Числовое значение, равное количеству секунд.  Должен указываться, если используется аргумент `numMilli`.  
  
 `numMilli`  
 Необязательный.  Числовое значение, равное количеству миллисекунд.  
  
## Заметки  
 Все методы **set**, принимающие необязательные аргументы, в случае, когда необязательный аргумент не задан, используют значение, возвращаемое соответствующими методами **get**.  Например, если аргумент *numSeconds* не задан, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] использует значение, возвращаемое методом `getSeconds`.  
  
 Чтобы установить значение минут с помощью времени в формате UTC, используйте метод `setUTCMinutes`.  
  
 Если значение аргумента превышает верхнюю границу его диапазона или является отрицательным числом, остальные хранящиеся значения изменяются соответственно.  Например, если сохранена дата "00:00:00 5 января 1996 г." и вызывается метод **setMinutes\(90\)**, дата принимает значение "01:30:00 5 января 1996 г.". Отрицательные числа ведут себя аналогично.  
  
## Пример  
 В следующем примере показано использование метода `setMinutes`.  
  
```javascript  
function SetMinutesDemo(nmin, nsec){  
   var d, s;                     // Declare variables.  
   d = new Date();               // Create Date object.  
   d.setMinutes(nmin, nsec);     // Set minutes.  
   s = "Current setting is " + d.toLocaleString()   
   return(s);                    // Return new setting.  
}  
```  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Относится к**: [Объект Date](../../javascript/reference/date-object-javascript.md)  
  
## См. также  
 [Метод getMinutes \(Date\)](../../javascript/reference/getminutes-method-date-javascript.md)   
 [Метод getUTCMinutes \(Date\)](../../javascript/reference/getutcminutes-method-date-javascript.md)   
 [Метод setUTCMinutes \(Date\)](../../javascript/reference/setutcminutes-method-date-javascript.md)