---
title: "Свойство constructor (Array) | Microsoft Docs"
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
ms.assetid: b78d517b-cb56-4866-b30f-ef8121a27843
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Свойство constructor (Array)
Указывает функцию, которая создает массив.  
  
## Синтаксис  
  
```  
  
array.constructor  
```  
  
## Заметки  
 Обязательный аргумент `array` представляет собой имя массива.  
  
 Свойство `constructor` является членом прототипа каждого объекта, у которого есть прототип.  Это включает все встроенные объекты [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], за исключением объектов `Global` и `Math`.  Свойство `constructor` содержит ссылку на функцию, которая создает экземпляры данного конкретного объекта.  
  
## Пример  
 В следующем примере кода демонстрируется использование свойства constructor.  
  
```javascript  
var x = new Array();  
  
if (x.constructor == Array)  
    document.write("Object is an Array.");  
else  
    document.write("Object is not an Array.");  
  
// Output:  
// Object is an Array.  
  
```  
  
## Требования  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]