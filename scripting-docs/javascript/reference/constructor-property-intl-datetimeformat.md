---
title: "Свойство constructor (Intl.DateTimeFormat) | Microsoft Docs"
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
ms.assetid: b72cebe3-20b5-4c86-9a5e-3819c11496c4
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Свойство constructor (Intl.DateTimeFormat)
Указывает функцию, которая создает модуль форматирования.  
  
## Синтаксис  
  
```javascript  
dateTimeFormatter.constructor  
```  
  
## Заметки  
 Требуемый элемент `dateTimeFormatter` — это имя модуля форматирования.  
  
 Свойство `constructor` является членом прототипа каждого объекта, у которого есть прототип.  Сюда входят все встроенные объекты JavaScript, за исключением объектов `Global` и `Math`.  Свойство `constructor` содержит ссылку на функцию, которая создает экземпляры данного конкретного объекта.  
  
## Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]