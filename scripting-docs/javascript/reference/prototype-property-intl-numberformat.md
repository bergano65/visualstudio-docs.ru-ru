---
title: "Свойство prototype (Intl.NumberFormat) | Microsoft Docs"
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
ms.assetid: 7f6a7e26-108b-4b32-97c2-7f96b9252c50
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Свойство prototype (Intl.NumberFormat)
Возвращает ссылку на прототип для модуля форматирования.  
  
## Синтаксис  
  
```javascript  
numberFormat.prototype  
```  
  
## Заметки  
 Аргумент `numberFormat` — это имя модуля форматирования.  
  
 Свойство `prototype` используется для предоставления базового набора функциональных возможностей классу объектов.  Новые экземпляры объекта "наследуют" поведение прототипа, присвоенного этому объекту.  
  
 Например, чтобы добавить в объект `Intl.NumberFormat` метод, возвращающий значение наибольшего элемента набора, объявите функцию, добавьте ее в свойство `Intl.NumberFormat.prototype`, а затем используйте ее.  
  
## Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]