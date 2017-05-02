---
title: "Метод toGMTString (Date) (JavaScript) | Microsoft Docs"
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
  - "toGMTString"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toGMTString - метод"
ms.assetid: 9dc1e722-5722-4b8c-a213-a2650f55f207
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Метод toGMTString (Date) (JavaScript)
Возвращает дату, преобразованную в строку с использованием времени по Гринвичу \(GMT\).  
  
## Синтаксис  
  
```  
  
dateObj.toGMTString()   
```  
  
## Заметки  
 Обязательная ссылка `dateObj` — это любой объект `Date`.  
  
 Метод `toGMTString` является устаревшим и предоставляется только для обеспечения обратной совместимости.  Рекомендуется использовать вместо него метод `toUTCString`.  
  
 Метод `toGMTString` возвращает объект `String`, который содержит дату в формате, соответствующем стандарту GMT.  Возвращаемое значение имеет следующий формат: "05 янв. 1996 00:00:00 GMT".  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Относится к**: [Объект Date](../../javascript/reference/date-object-javascript.md)  
  
## См. также  
 [Метод toUTCString \(Date\)](../../javascript/reference/toutcstring-method-date-javascript.md)