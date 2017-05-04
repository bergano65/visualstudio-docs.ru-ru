---
title: "Метод toLowerCase (JavaScript) | Microsoft Docs"
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
  - "toLowerCase"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toLowerCase - метод"
ms.assetid: dfd543b9-3e7a-4f83-a391-9cde109ad6bc
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Метод toLowerCase (JavaScript)
Преобразует все буквы в строке к нижнему регистру.  
  
## Синтаксис  
  
```  
  
      strVariable.toLowerCase()  
"String Literal".toLowerCase()   
```  
  
## Заметки  
 Метод `toLowerCase` не применяется к знакам, отличным от букв.  
  
 В следующем примере демонстрируется действие метода `toLowerCase`.  
  
```javascript  
var str1 = "This is a STRING.";  
var str2 = str1. toLowerCase();  
document.write(str2);  
  
// Output: this is a string.  
  
```  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Применение**: [Объект String](../../javascript/reference/string-object-javascript.md)  
  
## См. также  
 [Метод toLocaleLowerCase \(String\)](../../javascript/reference/tolocalelowercase-method-string-javascript.md)   
 [Метод toUpperCase \(String\)](../../javascript/reference/touppercase-method-string-javascript.md)