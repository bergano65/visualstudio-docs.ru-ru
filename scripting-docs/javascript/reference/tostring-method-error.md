---
title: "Метод toString (Error) | Microsoft Docs"
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
ms.assetid: 5d6d9712-c06d-4b31-9bc9-e46f6bb5cd38
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Метод toString (Error)
Возвращает строковое представление ошибки.  
  
## Синтаксис  
  
```  
  
error.toString()  
```  
  
## Параметры  
 `date`  
 Обязательный.  Ошибка, которую необходимо представить в виде строки.  
  
## Возвращаемое значение  
 Возвращает "Error: " и сообщение об ошибке.  
  
## Пример  
 В следующем примере показано использование метода `toString` применительно к ошибке.  
  
```javascript  
var myError = new Error();  
myError.message = "My Error";  
var errorString = myError.toString();  
document.write(errorString);  
  
// Output: Error: My Error  
  
```  
  
## Требования  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]