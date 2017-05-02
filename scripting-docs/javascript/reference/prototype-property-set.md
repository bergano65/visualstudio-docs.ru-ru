---
title: "Свойство prototype (Set) | Microsoft Docs"
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
ms.assetid: a075d5a6-e502-4636-85fc-1af001b8ac35
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Свойство prototype (Set)
Возвращает ссылку на прототип для набора.  
  
## Синтаксис  
  
```javascript  
set.prototype  
```  
  
## Заметки  
 Аргумент `set` — это имя набора.  
  
 Свойство `prototype` используется для предоставления базового набора функциональных возможностей классу объектов.  Новые экземпляры объекта "наследуют" поведение прототипа, присвоенного этому объекту.  
  
 Например, чтобы добавить в объект `Set` метод, возвращающий значение наибольшего элемента набора, объявите функцию, добавьте ее в свойство `Set.prototype`, а затем используйте ее.  
  
## Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]