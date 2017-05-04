---
title: "Свойство format (Intl.DateTimeFormat) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 487930fe-a948-446f-902d-06bb0d7685d5
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Свойство format (Intl.DateTimeFormat)
Возвращает функцию, которая форматирует дату, соответствующую языковому стандарту, используя настройки заданного средства форматирования даты\/времени.  
  
## Синтаксис  
  
```  
dateTimeFormatObj.format  
```  
  
#### Параметры  
 `dateTimeFormatObj`  
 Обязательное.  Имя объекта `DateTimeFormat` для использования в качестве средства форматирования.  
  
## Заметки  
 Функция, возвращаемая свойством `format`, принимает один аргумент — `date` — и возвращает строку, представляющую локализованную дату, с использованием параметров, заданных в объекте `DateTimeFormat`.  Параметр `date` возвращенной функции должен быть числом, строкой даты или объектом `Date`.  Если `date` не предоставляется, функция использует [Date.now](../../javascript/reference/date-now-function-javascript.md) как входное значение по умолчанию.  
  
## Пример  
 В следующем примере объект `DateTimeFormat` используется для локализации даты "Dec 1, 2007" на немецкий язык и ее переформатирования.  
  
```javascript  
var dtFormat = new Intl.DateTimeFormat(["de"], {  
    year: "numeric",  
    month: "long",  
    day: "2-digit",  
    hour: "numeric"  
});  
  
if (console && console.log) {  
    console.log(dtFormat.format(new Date("Dec 1, 2007")));  
    // Returns 01. Dezember 2007 00:00  
}  
```  
  
## Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## См. также  
 [Объект Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md)