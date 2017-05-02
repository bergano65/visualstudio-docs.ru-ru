---
title: "Метод toString (Number) | Microsoft Docs"
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
ms.assetid: 07c3484b-d9d8-4451-a2be-88a19a081966
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Метод toString (Number)
Возвращает строковое представление числа.  
  
## Синтаксис  
  
```  
  
number.toString()  
```  
  
## Параметры  
 `number`  
 Обязательный.  Число, которое необходимо представить в виде строки.  
  
## Возвращаемое значение  
 Строковое представление числа.  
  
## Пример  
 В следующем примере показано использование метода **toString** с числом.  
  
```javascript  
var number = 234.567;  
var s = number.toString();  
document.write(s.length);  
  
// Output: 7  
  
```  
  
## Требования  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]