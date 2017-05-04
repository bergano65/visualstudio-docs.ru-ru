---
title: "Метод getUTCSeconds (Date) (JavaScript) | Microsoft Docs"
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
  - "getUTCSeconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "время в формате UTC, возврат"
  - "seconds - метод"
  - "getUTCSeconds - метод"
ms.assetid: 2d8ea7dc-79f8-4a9b-b2ab-732db2bcd5fd
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Метод getUTCSeconds (Date) (JavaScript)
Возвращает секунды с помощью объекта `Date` универсальному времени \(UTC\).  
  
## Синтаксис  
  
```  
  
dateObj.getUTCSeconds()   
```  
  
#### Параметры  
 Обязательная ссылка `dateObj` объект `Date`.  
  
## Возвращаемое значение  
 Возвращает целое число в диапазоне от 0 до 59.  Ноль, если время меньше одной секунды в текущей минуте.  `Date` если объект был создан без указания времени, то по умолчанию используется значение 0 секунд времени в формате UTC.  
  
## Заметки  
 Чтобы получить количество секунд локального времени, используйте метод `getSeconds`.  
  
## Пример  
 В следующем примере показано, как использовать метод `getUTCSeconds`.  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date. getUTCSeconds());  
  
// Output: 0  
  
```  
  
## Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Applies To**: [Объект Date](../../javascript/reference/date-object-javascript.md)  
  
## См. также  
 [Метод getSeconds \(Date\)](../../javascript/reference/getseconds-method-date-javascript.md)   
 [Метод setSeconds \(Date\)](../../javascript/reference/setseconds-method-date-javascript.md)   
 [Метод setUTCSeconds \(Date\)](../../javascript/reference/setutcseconds-method-date-javascript.md)