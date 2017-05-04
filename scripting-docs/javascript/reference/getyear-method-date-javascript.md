---
title: "Метод getYear (Date) (JavaScript) | Microsoft Docs"
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
  - "getYear"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "даты, возврат года"
  - "GetYear - метод"
ms.assetid: 0e23e832-acd4-49a9-a175-515d0094f172
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# Метод getYear (Date) (JavaScript)
Возвращает год объекта `Date`.  
  
## Синтаксис  
  
```  
  
dateObj.getYear()   
```  
  
#### Параметры  
 Обязательная ссылка `dateObj` объект `Date`.  
  
## Возвращаемое значение  
 Возвращает год.  
  
## Заметки  
  
> [!IMPORTANT]
>  Этот метод устарел и предоставляется только для обеспечения обратной совместимости.  Взамен рекомендуется использовать метод `getFullYear`.  
  
 В [!INCLUDE[jsv1textspecific](../../javascript/reference/includes/jsv1textspecific-md.md)], а затем Internet Explorer в версиях, начинающихся с [!INCLUDE[jsv9textspecific](../../javascript/reference/includes/jsv9textspecific-md.md)], возвращаемое значение, хранящееся год минус 1900.  Например, 1899 год возвращается как \-1, а 2000 год возвращается как 100.  
  
 В [!INCLUDE[jsv3textspecific](../../javascript/reference/includes/jsv3textspecific-md.md)] через [!INCLUDE[jsv58textspecific](../../javascript/reference/includes/jsv58textspecific-md.md)], зависит от формулы год.  Для годов 1900 до 1999, возвращаемое значение \- значением 2 цифр, сохраненные год минус 1900.  Для дат за год, в диапазоне, возвращается 4 цифр.  Например, 1996 возвращается как 96, а 1825 и 2025 возвращаются в виде.  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Applies To**: [Объект Date](../../javascript/reference/date-object-javascript.md)  
  
## См. также  
 [Метод getFullYear \(Date\)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [Метод getUTCFullYear \(Date\)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [Метод setFullYear \(Date\)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [Метод setUTCFullYear \(Date\)](../../javascript/reference/setutcfullyear-method-date-javascript.md)   
 [Метод setYear \(Date\)](../../javascript/reference/setyear-method-date-javascript.md)