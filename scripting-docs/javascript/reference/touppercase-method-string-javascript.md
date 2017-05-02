---
title: "Метод toUpperCase (String) (JavaScript) | Microsoft Docs"
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
  - "toUpperCase"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toUpperCase - метод"
ms.assetid: 4fd4ccc3-e794-498a-9db1-baf48fc1dda1
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Метод toUpperCase (String) (JavaScript)
Преобразует все буквы в строке к прописным.  
  
## Синтаксис  
  
```  
  
      strVariable.toUpperCase()  
"String Literal".toUpperCase()   
```  
  
## Заметки  
 Метод `toUpperCase` не применяется к знакам, отличным от букв.  
  
## Пример  
 В следующем примере демонстрируется действие метода `toUpperCase`.  
  
```javascript  
var str1 = "This is a STRING.";  
var str2 = str1.toUpperCase();  
document.write(str2);  
  
// Output: THIS IS A STRING.  
  
```  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Применение**: [Объект String](../../javascript/reference/string-object-javascript.md)  
  
## См. также  
 [Метод toLocaleUpperCase \(String\)](../../javascript/reference/tolocaleuppercase-method-string-javascript.md)   
 [Метод toLowerCase](../../javascript/reference/tolowercase-method-javascript.md)