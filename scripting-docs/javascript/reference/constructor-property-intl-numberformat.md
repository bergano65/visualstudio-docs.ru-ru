---
title: "Свойство constructor (Intl.NumberFormat) | Microsoft Docs"
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
ms.assetid: ec35a7af-b29f-4fa5-8043-4126590ab6b5
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Свойство constructor (Intl.NumberFormat)
Указывает функцию, которая создает модуль форматирования.  
  
## Синтаксис  
  
```javascript  
numberFormatter.constructor  
```  
  
## Заметки  
 Требуемый элемент `numberFormatter` — это имя модуля форматирования.  
  
 Свойство `constructor` является членом прототипа каждого объекта, у которого есть прототип.  Сюда входят все встроенные объекты JavaScript, за исключением объектов `Global` и `Math`.  Свойство `constructor` содержит ссылку на функцию, которая создает экземпляры данного конкретного объекта.  
  
## Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]