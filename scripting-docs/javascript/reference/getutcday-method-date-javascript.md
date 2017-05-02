---
title: "Метод getUTCDay (Date) (JavaScript) | Microsoft Docs"
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
  - "getUTCDay"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date - объект"
  - "даты, формат UTC"
  - "даты в формате UTC, возврат"
  - "getUTCDay - метод"
ms.assetid: 2fceb5b0-6f77-4919-82c3-0877fd55bacb
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Метод getUTCDay (Date) (JavaScript)
Получает день недели, используя время в формате UTC.  
  
## Синтаксис  
  
```  
  
dateObj.getUTCDay()   
```  
  
#### Параметры  
 Обязательная ссылка `dateObj` — это объект `Date`.  
  
## Возвращаемое значение  
 Возвращает целое число от 0 \(воскресенье\) до 6 \(суббота\), представляющее день недели.  
  
## Заметки  
 Чтобы получить день недели с использованием местного времени, примените метод `getDate`.  
  
## Пример  
 В следующем примере показано использование метода `getUTCDay`.  
  
```javascript  
var date = new Date("2/6/2001");  
var day = date.getUTCDay();  
document.write(day);  
  
// Output: 2  
  
```  
  
## Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Относится к**: [Объект Date](../../javascript/reference/date-object-javascript.md)  
  
## См. также  
 [Метод getDay \(Date\)](../../javascript/reference/getday-method-date-javascript.md)