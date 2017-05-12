---
title: "Свойство prototype (WeakSet) | Microsoft Docs"
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
ms.assetid: 950e15a2-2f56-4cb9-8e48-020efd97f938
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Свойство prototype (WeakSet)
Возвращает ссылку на прототип для `WeakSet`.  
  
## Синтаксис  
  
```javascript  
weakset.prototype  
```  
  
## Заметки  
 Аргумент `weakset` является именем набора.  
  
 Чтобы для класса объектов обеспечить базовый набор функциональности, используйте свойство `prototype`.  Новые экземпляры объекта "наследуют" поведение прототипа, назначенного этому объекту.  
  
 Например, чтобы добавить метод в объект `WeakSet`, возвращающий значение самого большого элемента набора, объявите функцию, добавьте ее в `WeakSet.prototype`, а затем используйте ее.  
  
## Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]