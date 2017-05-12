---
title: "Метод getDate (Date) (JavaScript) | Microsoft Docs"
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
  - "getDate"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date - объект"
  - "даты, возврат дня месяца"
  - "getDate - метод"
ms.assetid: 67e7f07c-dd46-4b42-82d6-e53e4bd33703
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# Метод getDate (Date) (JavaScript)
Получает число месяца, используя местное время.  
  
## Синтаксис  
  
```  
  
dateObj.getDate()   
```  
  
#### Параметры  
 Обязательная ссылка `dateObj` — это объект `Date`.  
  
## Возвращаемое значение  
 Целое число от 1 до 31, представляющее число месяца.  
  
## Заметки  
 Чтобы получить число месяца в формате UTC, используйте метод `getUTCDate`.  
  
## Пример  
 В следующем примере показано использование метода `getDate`.  
  
```javascript  
var date = new Date("Jan 01, 2001");  
var str = "Today's date is: ";  
   str += (date.getMonth() + 1) + "/";  
   str += date.getDate() + "/";  
   str += date.getFullYear();  
document.write(str);  
  
// Output: Today's date is: 1/1/2001  
  
```  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Относится к**: [Объект Date](../../javascript/reference/date-object-javascript.md)  
  
## См. также  
 [Метод getUTCDate \(Date\)](../../javascript/reference/getutcdate-method-date-javascript.md)   
 [Метод setDate \(Date\)](../../javascript/reference/setdate-method-date-javascript.md)   
 [Метод setUTCDate \(Date\)](../../javascript/reference/setutcdate-method-date-javascript.md)