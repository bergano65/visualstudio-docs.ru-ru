---
title: "Метод setYear (Date) (JavaScript) | Microsoft Docs"
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
  - "setYear"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "setYear - метод"
  - "Year - метод"
ms.assetid: 36431050-e0ec-45ee-830d-0d7c20e207ea
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Метод setYear (Date) (JavaScript)
Устанавливает значение года в объекте `Date`.  
  
## Синтаксис  
  
```  
  
dateObj.setYear(numYear)   
```  
  
## Параметры  
 `dateObj`  
 Обязательный.  Любой объект `Date`.  
  
 `numYear`  
 Обязательный.  Для годов с 1900 по 1999 это числовое значение равно значению года минус 1900.  Для дат за пределами этого диапазона это 4\-значное числовое значение.  
  
## Заметки  
 Этот метод является устаревшим и сохраняется только для поддержки обратной совместимости.  Вместо него рекомендуется использовать метод `setFullYear`.  
  
 Чтобы задать для объекта `Date` 1997 год, вызовите метод **setYear\(97\)**.  Чтобы установить 2010 год, вызовите метод **setYear\(2010\)**.  И наконец, чтобы установить год в диапазоне от 0 до 99, используйте метод `setFullYear`.  
  
> [!NOTE]
>  В языке [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] версии 1.0 метод `setYear` использует значение, которое получается в результате прибавления значения 1900 к году, переданному в параметре `numYear`, независимо от фактического значения года.  Например, чтобы установить 1899 год, значение `numYear` должно быть равно \-1, а для указания 2000 года в параметре `numYear` необходимо передать значение 100.  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Относится к**: [Объект Date](../../javascript/reference/date-object-javascript.md)  
  
## См. также  
 [Метод getFullYear \(Date\)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [Метод getUTCFullYear \(Date\)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [Метод getYear \(Date\)](../../javascript/reference/getyear-method-date-javascript.md)   
 [Метод setFullYear \(Date\)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [Метод setUTCFullYear \(Date\)](../../javascript/reference/setutcfullyear-method-date-javascript.md)