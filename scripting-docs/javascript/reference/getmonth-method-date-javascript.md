---
title: "Метод getMonth (Date) (JavaScript) | Microsoft Docs"
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
  - "getMonth"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date - объект"
  - "даты, значение месяца"
  - "Month - метод"
  - "GetMonth - метод"
ms.assetid: c20dd8ba-1d78-42f1-8717-ed3dfd2362dd
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Метод getMonth (Date) (JavaScript)
Получает месяц по местному времени.  
  
## Синтаксис  
  
```  
  
dateObj.getMonth()   
```  
  
#### Параметры  
 Обязательная ссылка `dateObj` — это объект `Date`.  
  
## Возвращаемое значение  
 Метод `getMonth` возвращает целое число в диапазоне от 0 \(январь\) до 11 \(декабрь\).  Для объекта `Date` "Jan 5, 1996" метод `getMonth` возвращает 0.  
  
## Заметки  
 Чтобы получить значение месяца с использованием времени в формате UTC, используйте метод `getUTCMonth`.  
  
## Пример  
 В следующем примере показано использование метода `getMonth`.  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getMonth());  
  
// Output: 0  
```  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Относится к**: [Объект Date](../../javascript/reference/date-object-javascript.md)  
  
## См. также  
 [Метод getUTCMonth \(Date\)](../../javascript/reference/getutcmonth-method-date-javascript.md)   
 [Метод setMonth \(Date\)](../../javascript/reference/setmonth-method-date-javascript.md)   
 [Метод setUTCMonth \(Date\)](../../javascript/reference/setutcmonth-method-date-javascript.md)