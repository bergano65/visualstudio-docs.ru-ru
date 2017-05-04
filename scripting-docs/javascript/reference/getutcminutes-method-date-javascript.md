---
title: "Метод getUTCMinutes (Date) (JavaScript) | Microsoft Docs"
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
  - "getUTCMinutes"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "минуты"
  - "время в формате UTC, возврат"
  - "getUTCMinutes - метод"
ms.assetid: b6d92543-b285-4e46-8f47-bba36e53fabd
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Метод getUTCMinutes (Date) (JavaScript)
Возвращает минуты с помощью объекта `Date` универсальному времени \(UTC\).  
  
## Синтаксис  
  
```  
  
dateObj.getUTCMinutes()   
```  
  
#### Параметры  
 Обязательная ссылка `dateObj` объект `Date`.  
  
## Возвращаемое значение  
 Возвращает целое число в диапазоне от 0 до 59.  Ноль время меньше одной минуты после часа.  `Date` если объект был создан без указания времени, то по умолчанию используется значение минуты в формате UTC 0.  Однако в других часовых поясах оно может отличаться.  
  
## Заметки  
 Чтобы получить количество сохраненных минут с помощью локального времени, используйте метод `getMinutes`.  
  
## Пример  
 В следующем примере показано использование метода `getUTCMinutes`.  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getUTCMinutes());  
document.write("<br/>");  
  
date.setMinutes(5);  
document.write(date.getUTCMinutes());  
  
// Output:   
// 0  
// 5  
  
```  
  
## Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Applies To**: [Объект Date](../../javascript/reference/date-object-javascript.md)  
  
## См. также  
 [Метод getMinutes \(Date\)](../../javascript/reference/getminutes-method-date-javascript.md)   
 [Метод setMinutes \(Date\)](../../javascript/reference/setminutes-method-date-javascript.md)   
 [Метод setUTCMinutes \(Date\)](../../javascript/reference/setutcminutes-method-date-javascript.md)