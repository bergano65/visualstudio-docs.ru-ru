---
title: "Метод getUTCMonth (Date) (JavaScript) | Microsoft Docs"
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
  - "getUTCMonth"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "даты, формат UTC"
  - "даты в формате UTC, возврат"
  - "Month - метод"
  - "getUTCMonth - метод"
ms.assetid: eabae139-4da0-4e4a-a4cb-608e6375fc9e
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Метод getUTCMonth (Date) (JavaScript)
Возвращает месяц с помощью объекта `Date` универсальному времени \(UTC\).  
  
## Синтаксис  
  
```  
  
dateObj.getUTCMonth()   
```  
  
#### Параметры  
 Обязательная ссылка `dateObj` объект `Date`.  
  
## Возвращаемое значение  
 Возвращает целое число в диапазоне от 0 \(январь\) до 11 \(декабрь\).  
  
## Заметки  
 Чтобы получить значение месяца в локальном времени, используйте метод **getMonth**.  
  
## Пример  
 В следующем примере показано, как использовать метод `getUTCMonth`.  
  
```javascript  
var date = new Date("2/2/2002");  
document.write(date.getUTCMonth());  
  
// Output: 1  
  
```  
  
## Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Applies To**: [Объект Date](../../javascript/reference/date-object-javascript.md)  
  
## См. также  
 [Метод getMonth \(Date\)](../../javascript/reference/getmonth-method-date-javascript.md)   
 [Метод setMonth \(Date\)](../../javascript/reference/setmonth-method-date-javascript.md)   
 [Метод setUTCMonth \(Date\)](../../javascript/reference/setutcmonth-method-date-javascript.md)