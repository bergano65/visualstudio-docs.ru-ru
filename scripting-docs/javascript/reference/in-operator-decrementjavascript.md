---
title: "Оператор in (JavaScript) | Microsoft Docs"
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
  - "in_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "in - оператор"
ms.assetid: dcd8f901-96b8-4c91-848b-b1ec0ab1c11c
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Оператор in (JavaScript)
Проверяет существование свойства в объекте.  
  
## Синтаксис  
  
```  
  
result = property in object  
```  
  
## Параметры  
 `result`  
 Обязательный.  Любая переменная.  
  
 `property`  
 Обязательный.  Выражение, результатом вычисления которого является строковое выражение.  
  
 `object`  
 Обязательный.  Любой объект.  
  
## Заметки  
 Оператор `in` проверяет, содержит ли объект свойство с именем `property`.  Она также определяет, является ли свойство частью цепочки прототипов объекта.  Дополнительные сведения о прототипах объектов см. в разделе [Прототипы и их наследование](../../javascript/advanced/prototypes-and-prototype-inheritance.md).  
  
## Пример  
 В следующем примере показано, как использовать оператор `in`:  
  
```javascript  
// Create an object that has some properties.  
var myObject = new Object();  
myObject.name = "James";  
myObject.age = "22";  
myObject.phone = "555 0234";  
  
if ("phone" in myObject)  
   document.write ("property is present");  
else  
   document.write ("property is not present");  
  
// Output: property is present  
```  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## См. также  
 [Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md)   
 [Сводный список операторов \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)