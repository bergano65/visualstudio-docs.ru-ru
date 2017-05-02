---
title: "Метод toISOString (Date) (JavaScript) | Microsoft Docs"
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
helpviewer_keywords: 
  - "toISOString -метод [JavaScript]"
ms.assetid: 58577d8f-3ae8-4887-8687-26233ea79ff6
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Метод toISOString (Date) (JavaScript)
Возвращает дату в виде строкового значения в формате ISO.  
  
## Синтаксис  
  
```javascript  
  
objDate.toISOString()  
```  
  
## Возвращаемое значение  
 Строковое представление даты в формате Международной организации по стандартизации \(ISO\).  
  
## Исключения  
 Если `objDate` не содержит допустимую дату, то возникает исключение `RangeError`.  
  
## Заметки  
 Формат ISO представляет собой упрощенную версию формата ISO 8601.  Дополнительные сведения см. в разделе [Строки даты и времени](../../javascript/date-and-time-strings-javascript.md).  
  
 Временная зона — всегда UTC, на что указывает суффикс Z в выводе.  
  
## Пример  
 В следующем примере показано использование метода `toISOString`.  
  
```javascript  
var dt = new Date("30 July 2010 15:05 UTC");  
document.write(dt.toISOString());  
document.write("<br />");  
document.write(dt.toUTCString());  
  
// Output:  
//  2010-07-30T15:05:00.000Z  
//  Fri, 30 Jul 2010 15:05:00 UTC  
  
```  
  
## Требования  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## См. также  
 [Объект Date](../../javascript/reference/date-object-javascript.md)   
 [Строки даты и времени](../../javascript/date-and-time-strings-javascript.md)