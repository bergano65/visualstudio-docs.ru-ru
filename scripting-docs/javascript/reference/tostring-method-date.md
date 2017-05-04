---
title: "Метод toString (Date) | Microsoft Docs"
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
ms.assetid: d3037289-d805-409b-8781-045c59a2c404
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Метод toString (Date)
Возвращает строковое представление даты.  Формат строки зависит от языкового стандарта.  Для английского \(США\) \(en\-us\), он выглядит следующим образом:  
  
 *день недели* *месяц* *день* *час*. *минута*:*секунда* *часовой пояс* *год*  
  
## Синтаксис  
  
```  
  
date.toString()  
```  
  
## Параметры  
 `date`  
 Обязательное.  Дата для представления в виде строки.  
  
## Возвращаемое значение  
 Возвращает строковое представление даты.  
  
## Пример  
 В следующем примере показано, как использовать метод `toString` с датой.  
  
```javascript  
var myDate = new Date();  
myDate.setFullYear(2100, 5, 5);  
var dateString = myDate.toString();  
document.write(dateString);  
  
// Output: <date>  
  
```  
  
## Требования  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]