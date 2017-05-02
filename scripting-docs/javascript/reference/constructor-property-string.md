---
title: "Свойство constructor (String) | Microsoft Docs"
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
ms.assetid: ef0e9c82-4651-4404-87b1-d00cad38c6f9
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Свойство constructor (String)
Указывает функцию, которая создает строку.  
  
## Синтаксис  
  
```  
  
string.constructor  
```  
  
## Заметки  
 Обязательный аргумент `string` представляет собой имя строки.  
  
 Свойство `constructor` является членом прототипа каждого объекта, у которого есть прототип.  Это включает все встроенные объекты [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], за исключением объектов `Global` и `Math`.  Свойство `constructor` содержит ссылку на функцию, которая создает экземпляры данного конкретного объекта.  
  
## Пример  
 В следующем примере кода демонстрируется использование свойства constructor.  
  
```javascript  
var x = new String();  
  
if (x.constructor == String)  
    document.write("Object is a String.");  
else  
    document.write("Object is not a String.");  
  
// Output:  
// Object is a String.  
  
```  
  
## Требования  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]