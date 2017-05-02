---
title: "Метод getUTCFullYear (Date) (JavaScript) | Microsoft Docs"
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
  - "getUTCFullYear"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "getUTCFullYear - метод"
  - "Date - объект"
  - "UTCFullYear - метод"
  - "даты, формат UTC"
  - "даты в формате UTC, возврат"
  - "Full Year - метод"
  - "даты в формате UTC, получение"
ms.assetid: f11e5363-ef8a-48dd-9d56-4ee7290c7c48
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Метод getUTCFullYear (Date) (JavaScript)
Получает год, используя время в формате UTC.  
  
## Синтаксис  
  
```  
  
dateObj.getUTCFullYear()   
```  
  
#### Параметры  
 Обязательная ссылка `dateObj` — это объект `Date`.  
  
## Возвращаемое значение  
 Возвращает год в виде четырехзначного числа.  Предполагается, что годы, заданные двумя знаками в конструкторе `Date` или в `setFullYear`, относятся к двадцатому веку, поэтому для значения "5\/14\/12", `getUTCFullYear` возвращает 1912 год.  
  
## Заметки  
 Чтобы получить год с использованием местного времени, используйте метод `getFullYear`.  
  
## Пример  
 В следующем примере показано использование метода `getUTCFullYear`.  
  
```javascript  
var date = new Date("1/9/36");  
document.write(date.getUTCFullYear());  
  
// Output: 1936  
  
```  
  
## Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Относится к**: [Объект Date](../../javascript/reference/date-object-javascript.md)  
  
## См. также  
 [Метод getFullYear \(Date\)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [Метод setFullYear \(Date\)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [Метод setUTCFullYear \(Date\)](../../javascript/reference/setutcfullyear-method-date-javascript.md)