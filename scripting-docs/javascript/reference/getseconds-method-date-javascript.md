---
title: "Метод getSeconds (Date) (JavaScript) | Microsoft Docs"
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
  - "getSeconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "seconds - метод"
  - "GetSeconds - метод"
ms.assetid: 97b10674-af0b-4681-a846-38f972196501
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Метод getSeconds (Date) (JavaScript)
Возвращает секунды объекта `Date`, используя локальное время.  
  
## Синтаксис  
  
```  
  
dateObj.getSeconds()   
```  
  
#### Параметры  
 Обязательная ссылка `dateObj` объект `Date`.  
  
## Возвращаемое значение  
 Возвращает целое число в диапазоне от 0 до 59.  Ноль, если время меньше одной секунды в текущей минуте.  `Date` если объект был создан без указания времени, то по умолчанию используется значение 0 секунд.  
  
## Заметки  
 Для получения секунды значения, с помощью универсалию координировало времени \(UTC\) используют метод `getUTCSeconds`.  
  
## Пример  
 В следующем примере показано, как использовать метод `getSeconds`.  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getSeconds());  
document.write("<br/>");  
  
date.setSeconds(5);  
document.write(date.getSeconds());  
  
// Output:  
// 0  
// 5  
  
```  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Область применения.к**: [Объект Date](../../javascript/reference/date-object-javascript.md)  
  
## См. также  
 [Метод getUTCSeconds \(Date\)](../../javascript/reference/getutcseconds-method-date-javascript.md)   
 [Метод setSeconds \(Date\)](../../javascript/reference/setseconds-method-date-javascript.md)   
 [Метод setUTCSeconds \(Date\)](../../javascript/reference/setutcseconds-method-date-javascript.md)