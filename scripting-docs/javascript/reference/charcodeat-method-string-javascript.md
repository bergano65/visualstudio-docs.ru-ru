---
title: "Метод charCodeAt (String) (JavaScript) | Microsoft Docs"
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
  - "charCodeAt"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "charCodeAt - метод"
ms.assetid: 5b0290a7-ee4d-4738-a909-c02ef64a2f1a
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Метод charCodeAt (String) (JavaScript)
Возвращает значение символа Юникода в указанном расположении.  
  
## Синтаксис  
  
```  
  
strObj. charCodeAt(index)  
```  
  
## Параметры  
 `strObj`  
 Обязательный.  Любой объект `String` или строковый литерал.  
  
 `index`  
 Обязательный.  Индекс требуемого знака \(начиная с нуля\).  Если знак, соответствующий указанному индексу, отсутствует, возвращается значение `NaN`.  
  
## Заметки  
  
## Пример  
 В следующем примере показано использование метода `charCodeAt`.  
  
```javascript  
var str = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";   
document.write(str.charCodeAt(str.length - 1));  
  
// Output: 90   
```  
  
## Требования  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## См. также  
 [Функция String.fromCharCode](../../javascript/reference/string-fromcharcode-function-javascript.md)