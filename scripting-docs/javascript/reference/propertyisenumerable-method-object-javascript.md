---
title: "Метод propertyIsEnumerable (Object) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "propertyIsEnumerable"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "propertyIsEnumerable - свойство"
ms.assetid: d90c7c2e-ea23-4710-a957-9aefbbd1f68b
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Метод propertyIsEnumerable (Object) (JavaScript)
Определяет, является ли заданное свойство перечислимым.  
  
## Синтаксис  
  
```  
  
object. propertyIsEnumerable(proName)  
```  
  
## Параметры  
 `object`  
 Обязательный.  Экземпляр объекта.  
  
 `proName`  
 Обязательный.  Строковое значение имени свойства.  
  
## Заметки  
 Метод `propertyIsEnumerable` возвращает значение `true`, если свойство `proName` существует в объекте `object` и может перечисляться с помощью цикла `For`.  Метод `propertyIsEnumerable` возвращает значение `false`, если объект `object` не имеет свойства с указанным именем или если указанное свойство не является перечислимым.  Как правило, предопределенные свойства не являются перечислимыми, но свойства, определенные пользователем, всегда перечислимы.  
  
 Метод `propertyIsEnumerable` не учитывает объекты в цепи прототипов.  
  
## Пример  
  
```javascript  
var a = new Array("apple", "banana", "cactus");  
document.write(a.propertyIsEnumerable(1));  
  
// Output: true  
  
```  
  
## Требования  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## См. также  
 [Свойство prototype \(Object\)](../../javascript/reference/prototype-property-object-javascript.md)