---
title: "Метод includes (String) (JavaScript) | Microsoft Docs"
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
ms.assetid: 2639e4e5-23ba-424a-80ea-be067a4cd65e
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Метод includes (String) (JavaScript)
Возвращает логическое значение, указывающее, содержится ли переданная строка в объекте string.  
  
## Синтаксис  
  
```  
stringObj.includes(substring [, position]);  
```  
  
#### Параметры  
 `stringObj`  
 Обязательный.  Объект string, с использованием которого выполняется проверка.  
  
 `substring`  
 Обязательный.  Строка для проверки.  
  
 `position`  
 Необязательный.  Позиция первого символа для проверки в объекте string, начинающемся с 0.  
  
## Возвращаемое значение  
 Если переданная строка содержится в объекте string, метод `includes` возвращает `true`, а если нет, то `false`.  
  
## Заметки  
  
## Пример  
  
```javascript  
// Returns true   
"abcde".includes("cd")  
"abcde".includes("cd", 2)  
  
// Returns false  
"abcde".includes("CD")  
"abcde".includes("cd", 3)  
  
```  
  
## Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]