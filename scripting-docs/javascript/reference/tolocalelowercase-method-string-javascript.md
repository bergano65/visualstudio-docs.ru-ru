---
title: "Метод toLocaleLowerCase (String) (JavaScript) | Microsoft Docs"
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
  - "toLocaleLowerCase"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toLocaleLowerCase - метод"
ms.assetid: add894d3-d14a-4dbc-a9b9-7ad1d3a2e581
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Метод toLocaleLowerCase (String) (JavaScript)
Преобразует все буквенные символы в нижний регистр с учетом текущего языкового стандарта среды размещения.  
  
## Синтаксис  
  
```  
  
stringVar.toLocaleLowerCase( )  
```  
  
## Заметки  
 Обязательная ссылка `stringVar` может быть объектом `String` или строковым литералом.  
  
 Метод `toLocaleLowerCase` преобразует символы в строку с учетом текущего языкового стандарта среды размещения.  В большинстве случаев результат совпадает с результатом метода `toLowerCase`.  Результаты отличаются только в том случае, если правила языка противоречат обычным правилам сопоставления регистров в Юникоде.  
  
## Требования  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Относится к**: [Объект String](../../javascript/reference/string-object-javascript.md)  
  
## См. также  
 [Метод toLocaleUpperCase \(String\)](../../javascript/reference/tolocaleuppercase-method-string-javascript.md)   
 [Метод toLowerCase](../../javascript/reference/tolowercase-method-javascript.md)