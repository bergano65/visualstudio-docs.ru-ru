---
title: "Метод getFullYear (Date) (JavaScript) | Microsoft Docs"
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
  - "getFullYear"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "даты, возвращение года"
  - "Date - объект"
  - "getFullYear - метод"
ms.assetid: f9ec1262-02e9-4791-90b5-48f33b1dc4bc
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Метод getFullYear (Date) (JavaScript)
Получает год по местному времени.  
  
## Синтаксис  
  
```  
  
dateObj.getFullYear()   
```  
  
#### Параметры  
 Обязательная ссылка `dateObj` — это объект `Date`.  
  
## Возвращаемое значение  
 Год в виде четырехзначного числа.  Например, 1976 год возвращается как 1976.  Предполагается, что годы, заданные двумя знаками в конструкторе `Date` или в `setFullYear`, относятся к двадцатому веку, поэтому для значения "5\/14\/12", `getFullYear` возвращает 1912 год.  
  
## Заметки  
 Чтобы получить значение года с временем в формате UTC, используйте метод `getUTCFullYear`.  
  
## Пример  
 В следующем примере показано использование метода **getFullYear**.  
  
```javascript  
var date = new Date("1/1/01");  
document.write(date.getFullYear());  
  
// Output: 1901  
  
```  
  
## Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Относится к**: [Объект Date](../../javascript/reference/date-object-javascript.md)  
  
## См. также  
 [Метод getUTCFullYear \(Date\)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [Метод setFullYear \(Date\)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [Метод setUTCFullYear \(Date\)](../../javascript/reference/setutcfullyear-method-date-javascript.md)