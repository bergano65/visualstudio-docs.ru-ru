---
title: "Метод getUTCMilliseconds (Date) (JavaScript) | Microsoft Docs"
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
  - "getUTCMilliseconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "миллисекунды"
  - "время в формате UTC, возврат"
  - "getUTCMilliseconds - метод"
ms.assetid: 7491d387-7b6a-40df-89e5-55c64795ef70
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Метод getUTCMilliseconds (Date) (JavaScript)
Получает число миллисекунд объекта `Date` с помощью универсальному времени \(UTC\).  
  
## Синтаксис  
  
```  
  
dateObj.getUTCMilliseconds()   
```  
  
#### Параметры  
 Обязательная ссылка `dateObj` объект `Date`.  
  
## Возвращаемое значение  
 Возвращает значение миллисекунд, которое может варьироваться от 0\-999.  
  
## Заметки  
 Чтобы получить количество миллисекунд в локальном времени, используйте метод `getMilliseconds`.  
  
## Пример  
 В следующем примере показано использование метода `getUTCMilliseconds`.  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getUTCMilliseconds());  
document.write("<br/>");  
  
date.setMilliseconds(34);  
document.writedate.getUTCMilliseconds());  
  
// Output:  
// 0   
// 34   
```  
  
## Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Applies To**: [Объект Date](../../javascript/reference/date-object-javascript.md)  
  
## См. также  
 [Метод getMilliseconds \(Date\)](../../javascript/reference/getmilliseconds-method-date-javascript.md)   
 [Метод setMilliseconds \(Date\)](../../javascript/reference/setmilliseconds-method-date-javascript.md)   
 [Метод setUTCMilliseconds \(Date\)](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)