---
title: "Метод getMinutes (Date) (JavaScript) | Microsoft Docs"
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
  - "getMinutes"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "GetMinutes - метод"
  - "minutes - метод"
ms.assetid: d4139b5d-04e1-474c-9a83-e9d40597243a
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Метод getMinutes (Date) (JavaScript)
Получает минуты объекта `Date` по местному времени.  
  
## Синтаксис  
  
```  
  
dateObj.getMinutes()   
```  
  
#### Параметры  
 Обязательная ссылка `dateObj` — это объект `Date`.  
  
## Возвращаемое значение  
 Возвращает целое число от 0 до 59.  Ноль возвращается, если время в текущем часе меньше одной минуты.  Если объект `Date` был создан без указания времени, то по умолчанию используется значение 0 минут.  
  
## Заметки  
 Чтобы получить значение минут с использованием универсального времени UTC, используйте метод `getUTCMinutes`.  
  
## Пример  
 В следующем примере показано использование метода `getMinutes`.  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getMinutes());  
document.write("<br/>");  
  
date.setMinutes(5);  
document.write(date.getMinutes());  
  
// Output:  
// 0  
// 5  
  
```  
  
## Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Относится к**: [Объект Date](../../javascript/reference/date-object-javascript.md)  
  
## См. также  
 [Метод getUTCMinutes \(Date\)](../../javascript/reference/getutcminutes-method-date-javascript.md)   
 [Метод setMinutes \(Date\)](../../javascript/reference/setminutes-method-date-javascript.md)   
 [Метод setUTCMinutes \(Date\)](../../javascript/reference/setutcminutes-method-date-javascript.md)