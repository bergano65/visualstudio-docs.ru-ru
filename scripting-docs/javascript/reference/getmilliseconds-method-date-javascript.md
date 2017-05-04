---
title: "Метод getMilliseconds (Date) (JavaScript) | Microsoft Docs"
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
  - "getMilliseconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "миллисекунды"
  - "getMilliseconds - метод"
ms.assetid: 1b512146-1e8a-44a4-89da-6cc5338d15cb
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Метод getMilliseconds (Date) (JavaScript)
Получает значение даты в миллисекундах по местному времени.  
  
## Синтаксис  
  
```  
  
dateObj.getMilliseconds()   
```  
  
#### Параметры  
 Обязательная ссылка `dateObj` — это объект `Date`.  
  
## Возвращаемое значение  
 Возвращает миллисекунды даты.  Значение может находиться в диапазоне от 0 до 999.  Если дата была построена без указания миллисекунд, то возвращаемое значение равно 0.  
  
## Заметки  
 Для получения количества миллисекунд в формате UTC используется метод `getUTCMilliseconds`.  
  
## Пример  
 В следующем примере показано использование метода **getMilliseconds**.  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getMilliseconds());  
document.write("<br/>");  
  
date.setMilliseconds(5);  
document.write(date.getMilliseconds());  
// Output:   
// 0  
// 5  
  
```  
  
## Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Относится к**: [Объект Date](../../javascript/reference/date-object-javascript.md)  
  
## См. также  
 [Метод getUTCMilliseconds \(Date\)](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)   
 [Метод setMilliseconds \(Date\)](../../javascript/reference/setmilliseconds-method-date-javascript.md)   
 [Метод setUTCMilliseconds \(Date\)](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)