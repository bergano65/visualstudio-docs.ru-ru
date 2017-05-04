---
title: "Метод fill (Array) (JavaScript) | Microsoft Docs"
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
ms.assetid: 11526627-c0bb-4157-a8c4-0a039079b4a1
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Метод fill (Array) (JavaScript)
Заполняет массив указанным значением.  
  
## Синтаксис  
  
```  
arrayObj.fill(value [ , start [ , end ] ]);  
```  
  
#### Параметры  
 `arrayObj`  
 Обязательный.  Объект Array  
  
 `value`  
 Обязательный.  Значение, используемое для заполнения массива.  
  
 `start`  
 Необязательный.  Начальный индекс, используемый для заполнения массива значений.  Значение по умолчанию — 0.  
  
 `end`  
 Необязательный.  Конечный индекс, используемый для заполнения массива значений.  Значением по умолчанию является значение свойства length объекта `this`.  
  
## Заметки  
 Если значение `start` отрицательно, то `start` рассматривается как `length`\+`start`, где `length` соответствует длине массива \(свойство length\).  Если значение `end` отрицательно, `end` рассматривается как `length`\+`end`.  
  
## Пример  
 В следующих примерах кода массив заполняется значениями:  
  
```javascript  
[0, 0, 0].fill(7, 1);  
// Array contains [0,7,7]  
  
[0, 0, 0].fill(7);  
// Array contains [7,7,7]  
  
```  
  
## Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]