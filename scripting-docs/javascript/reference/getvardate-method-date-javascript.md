---
title: "Метод getVarDate (Date) (JavaScript) | Microsoft Docs"
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
  - "getVarDate"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date - объект"
  - "getVarDate - метод"
  - "даты, формат VT_DATE"
ms.assetid: 561238de-5c91-45a3-b839-a16910d3a1cf
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# Метод getVarDate (Date) (JavaScript)
Возвращает значение VT\_DATE из объекта `Date`.  
  
> [!WARNING]
>  Этот метод поддерживается только в Internet Explorer.  
  
## Синтаксис  
  
```  
  
dateObj.getVarDate()   
```  
  
#### Параметры  
 Обязательная ссылка `dateObj` — это объект `Date`.  
  
## Возвращаемое значение  
 Возвращает значение VT\_DATE.  
  
## Заметки  
 Метод `getVarDate` используется, когда код JavaScript взаимодействует с объектами COM, объектами ActiveX и другими объектами, которые принимают и возвращают значения даты в формате VT\_DATE. Сюда входят объекты в Visual Basic и Visual Basic Scripting Edition \(VBScript\). Фактический формат возвращаемого значения зависит от региональных параметров.  
  
## Требования  
 Поддерживается в следующих режимах документов: случайный режим, стандартный режим Internet Explorer 6, стандартный режим Internet Explorer 7, стандартный режим Internet Explorer 8, стандартный режим Internet Explorer 9, стандартный режим Internet Explorer 10. Не поддерживается в приложениях [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]. См. [Сведения о версии](../../javascript/reference/javascript-version-information.md).  
  
 **Применимо к**: [Объект Date](../../javascript/reference/date-object-javascript.md)  
  
## См. также  
 [Метод getDate \(Date\)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Функция Date.parse](../../javascript/reference/date-parse-function-javascript.md)