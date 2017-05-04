---
title: "Метод valueOf (Date) | Microsoft Docs"
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
ms.assetid: 39a1f96e-14b0-4db2-b53d-cdfd67cbb208
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Метод valueOf (Date)
Возвращает сохраненное значение времени, прошедшего после полуночи 1 января 1970 года \(UTC\) в миллисекундах.  
  
## Синтаксис  
  
```  
  
date.valueOf()  
```  
  
#### Параметры  
 Объект `date` — любой экземпляр Date.  
  
## Возвращаемое значение  
 Сохраненное значение времени, прошедшего после полуночи 1 января 1970 года \(UTC\) в миллисекундах.  Значение совпадает с `getTime`.  
  
## Пример  
 В следующем примере показано использование метода `valueOf` с датой.  
  
```javascript  
var myDate = new Date();  
myDate.setFullYear(2100, 5, 5);  
if (myDate.getTime() == myDate.valueOf())  
    document.write("values are the same");  
else  
    document.write("values are different");  
  
// Output: values are the same  
  
```  
  
## Требования  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]