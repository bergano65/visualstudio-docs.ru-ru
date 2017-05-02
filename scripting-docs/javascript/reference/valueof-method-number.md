---
title: "Метод valueOf (Number) | Microsoft Docs"
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
ms.assetid: 0242a9ce-d41a-4c9b-af59-e8df32bbd913
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Метод valueOf (Number)
Возвращает простое значение указанного числа.  
  
## Синтаксис  
  
```  
  
number.valueOf()  
```  
  
#### Параметры  
 Этот метод не имеет параметров.  
  
## Возвращаемое значение  
 Возвращает число.  
  
## Заметки  
 В следующем примере созданный экземпляр объекта числа совпадает с возвращаемым значением этого метода.  
  
```javascript  
var num = 1234;  
var s = num.valueOf();  
  
if (num === s)  
document.write("same");  
else  
document.write("different");  
  
// Output:  
// same  
  
```  
  
## Требования  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]