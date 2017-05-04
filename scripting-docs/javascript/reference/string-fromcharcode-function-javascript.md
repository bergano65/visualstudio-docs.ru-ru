---
title: "Функция String.fromCharCode (JavaScript) | Microsoft Docs"
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
  - "fromCharCode"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "fromCharCodeAt - метод"
  - "символы, из Юникода"
ms.assetid: f64120c1-23a7-48ca-8d1c-db3e8856cab4
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Функция String.fromCharCode (JavaScript)
Возвращает строку, содержащую набор значений знаков Юникода.  
  
## Синтаксис  
  
```  
String.fromCharCode([code1[, code2[, ...[, codeN]]]])   
```  
  
## Параметры  
 `String`  
 Обязательный.  Объект `String`.  
  
 `code1`, . . . , `codeN`  
 Необязательный.  Последовательность значений символов Юникода для преобразования в строку.  Если аргументы не указаны, результатом будет пустая строка.  
  
## Заметки  
 Эта функция вызывается для объекта `String`, а не для экземпляра строки.  
  
 В следующем примере показано, как использовать этот метод:  
  
```javascript  
var test = String.fromCharCode(112, 108, 97, 105, 110);  
document.write(test);  
  
// Output: plain  
  
```  
  
## Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## См. также  
 [Метод charCodeAt \(String\)](../../javascript/reference/charcodeat-method-string-javascript.md)