---
title: "Свойство prototype (WeakMap) | Microsoft Docs"
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
ms.assetid: d28b8a9b-38c9-443d-9586-7cc74784bd99
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Свойство prototype (WeakMap)
Возвращает ссылку на прототип для объекта `WeakMap`.  
  
## Синтаксис  
  
```javascript  
weakmap.prototype  
```  
  
## Заметки  
 Аргумент `weakmap` — это имя объекта `WeakMap`.  
  
 Свойство `prototype` используется для предоставления базового набора функциональных возможностей классу объектов.  Новые экземпляры объекта "наследуют" поведение прототипа, присвоенного этому объекту.  
  
 Например, чтобы добавить в объект `WeakMap` метод, возвращающий значение наибольшего элемента в `WeakMap`, объявите функцию, добавьте ее в свойство `WeakMap.prototype`, а затем используйте ее.  
  
## Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]