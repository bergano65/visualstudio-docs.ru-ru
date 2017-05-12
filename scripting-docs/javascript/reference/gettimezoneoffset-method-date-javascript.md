---
title: "Метод getTimezoneOffset (Date) (JavaScript) | Microsoft Docs"
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
  - "getTimeZoneOffset"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "getTimezoneOffset - метод"
  - "часовые пояса [Visual Studio]"
ms.assetid: 58ee22b0-4688-45bd-a337-cc23119b09ce
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Метод getTimezoneOffset (Date) (JavaScript)
Получает разницу в минутах между местным временем компьютера и временем в формате UTC.  
  
## Синтаксис  
  
```  
  
dateObj.getTimezoneOffset()   
```  
  
#### Параметры  
 Обязательная ссылка `dateObj` — это объект `Date`.  
  
## Возвращаемое значение  
 Возвращает количество минут между временем на текущем компьютере \(на клиентской машине или, если этот метод вызван из серверного скрипта, на серверной машине\) и временем в формате UTC.  Значение положительно, если местное время компьютера меньше времени в формате UTC \(например, Тихоокеанское время США\), и отрицательно, если местное время компьютера больше времени в формате UTC \(например, в Японии\).  Если к серверу в Нью\-Йорке отправлен запрос клиентом в Лос\-Анджелесе 1\-го декабря, то `getTimezoneOffset` возвращает 480, если выполняется на клиенте, или 300 при выполнении на сервере.  
  
## Заметки  
  
## Пример  
 В следующем примере показано использование метода `getTimezoneOffset`.  
  
```javascript  
var date =  new Date();  
var minutes = date.getTimezoneOffset();  
  
if (minutes < 0)  
    document.write(minutes / 60 + " hours after UTC");  
else  
    document.write(minutes / 60 + " hours before UTC");  
  
// Output (for example, where local time is PST):   
7 hours before UTC  
  
```  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Относится к**: [Объект Date](../../javascript/reference/date-object-javascript.md)  
  
## См. также  
 [Метод getTime \(Date\)](../../javascript/reference/gettime-method-date-javascript.md)