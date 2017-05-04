---
title: "Свойство constructor (Map) | Microsoft Docs"
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
ms.assetid: a90d6a29-bd64-4e01-8d2f-988b7e3e4a24
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Свойство constructor (Map)
Указывает функцию, которая создает сопоставление.  
  
## Синтаксис  
  
```javascript  
map.constructor  
```  
  
## Заметки  
 Требуемый элемент `map` — это имя сопоставления.  
  
 Свойство `constructor` является членом прототипа каждого объекта, у которого есть прототип.  Сюда входят все встроенные объекты JavaScript, за исключением объектов `Global` и `Math`.  Свойство `constructor` содержит ссылку на функцию, которая создает экземпляры данного конкретного объекта.  
  
## Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]