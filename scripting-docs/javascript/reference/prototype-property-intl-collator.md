---
title: "Свойство prototype (Intl.Collator) | Microsoft Docs"
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
ms.assetid: c1bbb523-fb55-4395-b357-34d91cf5bba0
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Свойство prototype (Intl.Collator)
Возвращает ссылку на прототип для средства упорядочения.  
  
## Синтаксис  
  
```javascript  
collator.prototype  
```  
  
## Заметки  
 Аргумент `collator` — это имя средства упорядочения.  
  
 Свойство `prototype` используется для предоставления базового набора функциональных возможностей классу объектов.  Новые экземпляры объекта "наследуют" поведение прототипа, присвоенного этому объекту.  
  
 Например, чтобы добавить в объект `Intl.Collator` метод, возвращающий значение наибольшего элемента набора, объявите функцию, добавьте ее в свойство `Intl.Collator.prototype`, а затем используйте ее.  
  
## Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]