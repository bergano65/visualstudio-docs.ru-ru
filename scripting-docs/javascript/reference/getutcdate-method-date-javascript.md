---
title: "Метод getUTCDate (Date) (JavaScript) | Microsoft Docs"
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
  - "getUTCDate"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date - объект"
  - "даты, формат UTC"
  - "даты в формате UTC, возврат"
  - "getUTCDate - метод"
ms.assetid: 9e4c763f-c94c-44c9-9684-cb632d75b62e
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Метод getUTCDate (Date) (JavaScript)
Получает число месяца в формате UTC.  
  
## Синтаксис  
  
```  
  
dateObj.getUTCDate()   
```  
  
#### Параметры  
 Обязательная ссылка `dateObj` — это объект `Date`.  
  
## Возвращаемое значение  
 Возвращает целое число от 1 до 31, представляющее число месяца.  
  
## Заметки  
 Чтобы получить день месяца с использованием местного времени, используйте метод `getDate`.  
  
## Пример  
 В следующем примере показано использование метода `getUTCDate`.  
  
```javascript  
var date = new Date("1/23/2001");  
document.write(date.getUTCDate());  
  
// Output: 23  
  
```  
  
## Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Относится к**: [Объект Date](../../javascript/reference/date-object-javascript.md)  
  
## См. также  
 [Метод getDate \(Date\)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Метод setDate \(Date\)](../../javascript/reference/setdate-method-date-javascript.md)   
 [Метод setUTCDate \(Date\)](../../javascript/reference/setutcdate-method-date-javascript.md)