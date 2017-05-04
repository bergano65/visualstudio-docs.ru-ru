---
title: "Метод getUTCHours (Date) (JavaScript) | Microsoft Docs"
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
  - "getUTCHours"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "часы"
  - "время в формате UTC, возврат"
  - "getUTCHours - метод"
ms.assetid: 7c9825dd-4b3a-4614-8e09-f40df123b630
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Метод getUTCHours (Date) (JavaScript)
Возвращает значение часов в объекте `Date` с помощью универсальному времени \(UTC\).  
  
## Синтаксис  
  
```  
  
dateObj.getUTCHours()   
```  
  
#### Параметры  
 Обязательная ссылка `dateObj` объект `Date`.  
  
## Возвращаемое значение  
 Возвращает целое число в диапазоне от 0 до 23, которое указывает количество часов, истекших после полуночи.  Ноль, если время до 1:00: 00 am.  `Date` если объект был создан без указания времени, то по умолчанию часа 0 в формате UTC.  Это время может иметь ненулевое значение в других часовых поясах.  
  
## Заметки  
 Чтобы получить количество часов, истекших после полуночи, с помощью локального времени, используйте метод `getHours`.  
  
## Пример  
 В следующем примере показано использование метода `getUTCHours`.  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getUTCHours());  
document.write("<br/>");  
  
var date2 = new Date("1/1/2001 11:22:33");  
document.write(datee.getUTCHours());  
  
// Output (in the PST time zone):  
// 8  
// 19  
  
```  
  
## Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Applies To**: [Объект Date](../../javascript/reference/date-object-javascript.md)  
  
## См. также  
 [Метод getHours \(Date\)](../../javascript/reference/gethours-method-date-javascript.md)   
 [Метод setHours \(Date\)](../../javascript/reference/sethours-method-date-javascript.md)   
 [Метод setUTCHours \(Date\)](../../javascript/reference/setutchours-method-date-javascript.md)