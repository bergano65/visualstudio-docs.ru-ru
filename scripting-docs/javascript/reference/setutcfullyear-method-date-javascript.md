---
title: "Метод setUTCFullYear (Date) (JavaScript) | Microsoft Docs"
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
  - "setUTCFullYear"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "даты, время в формате UTC"
  - "setUTCFullYear - метод"
  - "даты в формате UTC, параметр"
ms.assetid: e6c51b49-0149-4f9a-aa74-c73c0306f98e
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Метод setUTCFullYear (Date) (JavaScript)
Устанавливает значение года в объекте `Date`, используя универсальное время UTC.  
  
## Синтаксис  
  
```  
  
dateObj.setUTCFullYear(numYear[, numMonth[, numDate]])   
```  
  
## Параметры  
 `dateObj`  
 Обязательный.  Любой объект `Date`.  
  
 `numYear`  
 Обязательный.  Числовое значение, представляющее год.  
  
 `numMonth`  
 Необязательный.  Числовое значение, равное месяцу.  Значение для января равно 0, значения других месяцев увеличиваются соответственно.  Должен указываться, если указывается аргумент *numDate*.  
  
 *numDate*  
 Необязательный.  Числовое значение, обозначающее день месяца.  
  
## Заметки  
 Все методы **set**, принимающие необязательные аргументы, в случае, когда необязательный аргумент не задан, используют значение, возвращаемое соответствующими методами **get**.  Например, если аргумент `numMonth` не задан, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] использует значение, возвращенное методом `getUTCMonth`.  
  
 Кроме того, если значение аргумента превышает верхнюю границу его диапазона или является отрицательным числом, остальные хранящиеся значения изменяются соответственно.  
  
 Чтобы установить год с использованием местного времени, используйте метод `setFullYear`.  
  
 Диапазон лет, поддерживаемых в объекте `Date`, равен приблизительно 285 616 годам в каждую сторону от 1970 года.  
  
## Пример  
 В следующем примере показано использование метода `setUTCFullYear`.  
  
```javascript  
var dtFirst = new Date();  
dtFirst.setUTCFullYear(2007);  
  
var dtSecond = new Date();  
// 10 is the value for November.   
dtSecond.setUTCFullYear(2008, 10, 3);   
  
document.write (dtFirst.toUTCString());  
document.write ("<br />");  
document.write (dtSecond.toUTCString());  
```  
  
## Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Относится к**: [Объект Date](../../javascript/reference/date-object-javascript.md)  
  
## См. также  
 [Метод getFullYear \(Date\)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [Метод getUTCFullYear \(Date\)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [Метод setFullYear \(Date\)](../../javascript/reference/setfullyear-method-date-javascript.md)