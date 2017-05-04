---
title: "Метод getDay (Date) (JavaScript) | Microsoft Docs"
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
  - "getDay"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "GetDay - метод"
  - "Date - объект"
  - "даты, возврат дня недели"
ms.assetid: 27be7168-3dce-41c9-ae69-6280b7984c2e
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Метод getDay (Date) (JavaScript)
Получает день недели, используя местное время.  
  
## Синтаксис  
  
```  
  
dateObj. getDay()   
```  
  
#### Параметры  
 Обязательная ссылка `dateObj` — это объект `Date`.  
  
## Возвращаемое значение  
 Целое число от 0 до 6, представляющее день недели \(воскресенье — 0, суббота — 6\).  
  
## Заметки  
 Для получения дня с использованием времени в формате UTC используется метод `getUTCDay`.  
  
 В следующем примере показано использование метода `getDay`.  
  
```javascript  
var date = new Date("Saturday, February 9, 2008");  
day = date.getDay();  
document.write(day);  
  
// Output: 6  
  
```  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Относится к**: [Объект Date](../../javascript/reference/date-object-javascript.md)  
  
## См. также  
 [Метод getUTCDay \(Date\)](../../javascript/reference/getutcday-method-date-javascript.md)