---
title: "Метод delete (Set) (JavaScript) | Microsoft Docs"
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
ms.assetid: 052c409e-10c9-49f2-955d-5ad7e31c14f3
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Метод delete (Set) (JavaScript)
Удаляет указанный элемент из набора.  
  
## Синтаксис  
  
```javascript  
setObj.delete(value)  
```  
  
#### Параметры  
 `setObj`  
 Обязательное.  Объект `Set`.  
  
 `value`  
 Обязательное.  Подлежащий удалению элемент.  
  
## Значение свойства или возвращаемое значение  
 Значение `true`, если элемент удален.  
  
## Пример  
 В следующем примере показано, как добавить члены в `Set` и затем удалить один из них.  
  
```javascript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
s.delete("founding father");  
  
s.forEach(function (item) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776,  
```  
  
## Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]