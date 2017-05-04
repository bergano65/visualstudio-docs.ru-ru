---
title: "Метод toString (Boolean) | Microsoft Docs"
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
ms.assetid: c46b43c0-6946-407a-b0e0-49cba90e226a
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Метод toString (Boolean)
Возвращает строковое представление объекта.  
  
## Синтаксис  
  
```  
  
boolean.toString()  
```  
  
## Параметры  
 `boolean`  
 Обязательный.  Объект, для которого требуется получить строковое представление.  
  
## Возвращаемое значение  
 Если логическое значение равно `true`, возвращается строка "true".  В противном случае возвращается строка "false".  
  
## Заметки  
  
## Пример  
 В следующем примере показано использование метода **toString**.  
  
```javascript  
var s = new Boolean(0);  
document.write(s.toString());  
  
// Output: false;  
  
```  
  
## Требования  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]