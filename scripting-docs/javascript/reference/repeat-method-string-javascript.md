---
title: "Метод repeat (String) (JavaScript) | Microsoft Docs"
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
ms.assetid: fe02cdfd-f0f6-45a2-ad36-31c4300ef142
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Метод repeat (String) (JavaScript)
Возвращает новый объект string со значением, равным исходной строке, повторенной указанное число раз.  
  
## Синтаксис  
  
```  
stringObj.repeat(count);  
```  
  
#### Параметры  
 `stringObj`  
 Обязательный.  Объект строки.  
  
 `count`  
 Обязательный.  Число повторений исходной строки в возвращаемой строке.  
  
## Исключения  
 Этот метод вызывает ошибку RangeError только в том случае, если аргумент представляет собой отрицательное число или \+бесконечность.  
  
## Заметки  
 Метод `repeat` объединяет исходную и новую строку столько раз, сколько указывает параметр `count`.  
  
 Этот метод вызывает ошибку, если `count` — не положительное число меньше `Infinity`.  
  
## Пример  
  
```javascript  
"abc".repeat(3); // Returns "abcabcabc"  
"abc".repeat(0); // Returns an empty string.  
```  
  
## Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]