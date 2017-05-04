---
title: "Метод has (Map) (JavaScript) | Microsoft Docs"
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
ms.assetid: 876df854-2941-4db2-92c6-1b497840b169
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Метод has (Map) (JavaScript)
Возвращает значение `true`, если сопоставление содержит указанный элемент.  
  
## Синтаксис  
  
```javascript  
mapObj.has(key)  
```  
  
#### Параметры  
 `mapObj`  
 Обязательное.  Объект `Map`.  
  
 `key`  
 Обязательное.  Ключ элемента, который требуется протестировать.  
  
## Значение свойства или возвращаемое значение  
 Значение `true`, если сопоставление содержит указанный элемент.  
  
## Пример  
 В следующем примере показано, как добавить член в `Map` и затем проверить, содержится ли он в карте.  
  
```javascript  
var m = new Map();  
m.set(2, "red");  
  
document.write(m.has(2));  
  
// Output:  
// true  
```  
  
## Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]