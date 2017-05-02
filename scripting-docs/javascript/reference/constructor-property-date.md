---
title: "Свойство constructor (Date) | Microsoft Docs"
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
ms.assetid: 5db153a1-788b-4a61-bfc8-2d2ec38f36ea
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Свойство constructor (Date)
Указывает функцию, которая создает дату.  
  
## Синтаксис  
  
```  
  
date.constructor  
```  
  
## Заметки  
 Обязательный аргумент `date` представляет собой объект даты.  
  
 Свойство `constructor` является членом прототипа каждого объекта, у которого есть прототип.  Свойство `constructor` содержит ссылку на функцию, которая создает экземпляры данного конкретного объекта.  
  
## Пример  
 В следующем примере кода демонстрируется использование свойства constructor.  
  
```javascript  
var x = new Date("Hi");  
  
if (x.constructor == Date)  
    document.write("Object is a date.");  
  
// Output:  
// Object is a date.  
  
```  
  
## Требования  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]