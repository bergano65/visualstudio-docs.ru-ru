---
title: "Метод toLocaleUpperCase (String) (JavaScript) | Microsoft Docs"
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
  - "toLocaleUpperCase"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toLocaleUpperCase - метод"
ms.assetid: e927adb6-475e-44b2-91f7-cedda10a39b0
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Метод toLocaleUpperCase (String) (JavaScript)
Возвращает строку, в которой все буквенные символы преобразованы в верхний регистр с учетом текущего языкового стандарта среды размещения.  
  
## Синтаксис  
  
```  
  
stringVar.toLocaleUpperCase( )  
```  
  
## Заметки  
 Обязательная ссылка `stringVar` может быть объектом `String` или строковым литералом.  
  
 Метод `toLocaleUpperCase` преобразует символы в строку с учетом текущего языкового стандарта среды размещения.  В большинстве случаев результат совпадает с результатом метода `toUpperCase`.  Результаты отличаются только в том случае, если правила языка противоречат обычным правилам сопоставления регистров в Юникоде.  
  
## Требования  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Относится к**: [Объект String](../../javascript/reference/string-object-javascript.md)  
  
## См. также  
 [Метод toLocaleLowerCase \(String\)](../../javascript/reference/tolocalelowercase-method-string-javascript.md)   
 [Метод toUpperCase \(String\)](../../javascript/reference/touppercase-method-string-javascript.md)