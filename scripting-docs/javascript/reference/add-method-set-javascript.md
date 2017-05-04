---
title: "Метод add (Set) (JavaScript) | Microsoft Docs"
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
ms.assetid: b4eea447-fd5b-4380-978e-1b95f6dbc438
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Метод add (Set) (JavaScript)
Добавляет новый элемент в набор.  
  
## Синтаксис  
  
```javascript  
setObj.add(value)  
```  
  
#### Параметры  
 `setObj`  
 Обязательный.  Объект `Set`.  
  
 `value`  
 Обязательный.  Новый элемент набора `Set`.  
  
## Заметки  
 Новый элемент может быть любого типа и должен быть уникальным.  При добавлении неуникального элемента в набор `Set` новый элемент не будет добавлен в коллекцию.  
  
## Пример  
 В следующем примере показано добавление членов в набор и затем извлечение их.  
  
```javascript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
  
s.forEach(function (item) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776, founding father,  
  
```  
  
## Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]