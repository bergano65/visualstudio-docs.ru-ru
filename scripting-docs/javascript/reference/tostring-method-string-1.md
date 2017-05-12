---
title: "Метод toString (String) | Microsoft Docs"
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
ms.assetid: 56178c6e-cb08-4b34-824c-f63505379952
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Метод toString (String)
Возвращает строковое представление строки.  
  
## Синтаксис  
  
```  
  
string.toString()  
```  
  
## Параметры  
 `string`  
 Обязательный.  Массив, который необходимо представить в виде строки.  
  
## Возвращаемое значение  
 Строковое представление строки.  
  
## Пример  
 В следующем примере показано использование метода **toString** со строкой.  
  
```javascript  
var string = "this is a test";  
var strStr = string.toString();  
document.write(strStr);  
  
// Output: this is a test  
  
```  
  
## Требования  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]