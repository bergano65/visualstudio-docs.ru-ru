---
title: "Свойство format (Intl.NumberFormat) | Microsoft Docs"
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
ms.assetid: 68c3223a-023c-4fa0-aa99-d049a7a0e26a
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Свойство format (Intl.NumberFormat)
Возвращает функцию, которая форматирует число, соответствующее языковому стандарту, используя настройки заданного средства форматирования числа.  
  
## Синтаксис  
  
```  
numberFormatObj.format  
```  
  
#### Параметры  
 `numberFormatObj`  
 Обязательное.  имя объекта `NumberFormat` для использования в качестве модуля форматирования.  
  
## Заметки  
 Функция, возвращаемая свойством `format`, принимает один аргумент — `value` — и возвращает строку, представляющую локализованное число, с использованием параметров, заданных в объекте `NumberFormat`.  Если `value` не предоставляется, функция возвращает `NaN` \(не число\).  
  
## Пример  
 Следующий пример использует объект `NumberFormat` для создания локализованного числа.  
  
```javascript  
var nf = new Intl.NumberFormat(["en-US"], {  
    style: "currency",  
    currency: "CNY",  
    currencyDisplay: "symbol",  
    maximumFractionDigit: 1  
})  
  
if (console && console.log) {  
    console.log(nf.format(100)); // "¥100.00"  
}  
  
```  
  
## Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## См. также  
 [Объект Intl.NumberFormat](../../javascript/reference/intl-numberformat-object-javascript.md)