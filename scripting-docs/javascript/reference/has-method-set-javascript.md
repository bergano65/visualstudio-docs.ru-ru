---
title: "Метод has (Set) (JavaScript) | Microsoft Docs"
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
ms.assetid: fb80f2e0-fc5e-4508-af14-1c3b3b833636
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Метод has (Set) (JavaScript)
Возвращает значение `true`, если набор содержит указанный элемент.  
  
## Синтаксис  
  
```javascript  
setObj.has(value)  
```  
  
#### Параметры  
 `setObj`  
 Обязательное.  Объект `Set`.  
  
 `value`  
 Обязательное.  Элемент для проверки.  
  
## Значение свойства или возвращаемое значение  
 Значение `true`, если набор содержит указанный элемент.  
  
## Пример  
 В следующем примере показано, как добавить члены в `Set` и затем проверить, содержит ли набор конкретный член.  
  
```javascript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
  
document.write(s.has(1776));  
document.write(s.has("1776"));  
  
// Output:  
// true  
// false  
  
```  
  
## Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]