---
title: "Свойство prototype (Intl.DateTimeFormat) | Microsoft Docs"
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
ms.assetid: e1e693ff-1775-407e-b655-18a60d238ded
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Свойство prototype (Intl.DateTimeFormat)
Возвращает ссылку на прототип для модуля форматирования.  
  
## Синтаксис  
  
```javascript  
dateTimeFormat.prototype  
```  
  
## Заметки  
 Аргумент `dateTimeFormat` — это имя модуля форматирования.  
  
 Свойство `prototype` используется для предоставления базового набора функциональных возможностей классу объектов.  Новые экземпляры объекта "наследуют" поведение прототипа, присвоенного этому объекту.  
  
 Например, чтобы добавить в объект `Intl.DateTimeFormat` метод, возвращающий значение наибольшего элемента набора, объявите функцию, добавьте ее в свойство `Intl.DateTimeFormat.prototype`, а затем используйте ее.  
  
## Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]