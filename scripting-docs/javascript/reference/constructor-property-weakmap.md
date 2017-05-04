---
title: "Свойство constructor (WeakMap) | Microsoft Docs"
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
ms.assetid: 1e3f9333-ce75-4d32-9b14-fbe81fd73dfb
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Свойство constructor (WeakMap)
Указывает функцию, которая создает объект `WeakMap`.  
  
## Синтаксис  
  
```javascript  
weakmap.constructor  
```  
  
## Заметки  
 Обязательный параметр `weakmap` — это имя объекта `WeakMap`.  
  
 Свойство `constructor` является членом прототипа каждого объекта, у которого есть прототип.  Сюда входят все встроенные объекты JavaScript, за исключением объектов `Global` и `Math`.  Свойство `constructor` содержит ссылку на функцию, которая создает экземпляры данного конкретного объекта.  
  
## Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]