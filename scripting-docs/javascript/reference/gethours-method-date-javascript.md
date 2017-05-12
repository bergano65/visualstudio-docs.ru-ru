---
title: "Метод getHours (Date) (JavaScript) | Microsoft Docs"
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
  - "getHours"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date - объект"
  - "GetHours - метод"
  - "Hours - метод"
ms.assetid: c3936496-a213-4d15-b308-d53926ed310c
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Метод getHours (Date) (JavaScript)
Получает часы в дате по местному времени.  
  
## Синтаксис  
  
```  
  
dateObj.getHours()   
```  
  
#### Параметры  
 Обязательная ссылка `dateObj` — это объект `Date`.  
  
## Возвращаемое значение  
 Целое число в диапазоне от 0 до 23, которое указывает количество часов, истекших после полуночи.  Ноль, если время до 01:00:00.  Если объект `Date` был создан без указания времени, то по умолчанию используется значение 0 часов.  
  
## Заметки  
 Чтобы получить значение часов с использованием времени в формате UTC, используйте метод `getUTCHours`.  
  
## Пример  
 В следующем примере показано использование метода `getHours`.  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getHours());  
document.write("<br/>");  
  
date.setTime(50000000);  
document.write(date.getHours());  
  
// Output:  
// 0   
// 5  
  
```  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Относится к**: [Объект Date](../../javascript/reference/date-object-javascript.md)  
  
## См. также  
 [Метод getUTCHours \(Date\)](../../javascript/reference/getutchours-method-date-javascript.md)   
 [Метод setHours \(Date\)](../../javascript/reference/sethours-method-date-javascript.md)   
 [Метод setUTCHours \(Date\)](../../javascript/reference/setutchours-method-date-javascript.md)