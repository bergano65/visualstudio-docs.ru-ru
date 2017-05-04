---
title: "Функция parseFloat (JavaScript) | Microsoft Docs"
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
  - "parseFloat"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "parseFloat - метод"
ms.assetid: a7d87a69-1919-4623-be85-972e6376dd2d
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Функция parseFloat (JavaScript)
Преобразует строку в число с плавающей запятой.  
  
## Синтаксис  
  
```  
parseFloat(numString)   
```  
  
## Заметки  
 Обязательный аргумент `numString` — это строка, содержащая число с плавающей запятой.  
  
 Функция `parseFloat` возвращает числовое значение, которое равно числу, содержащемуся в строке `numString`.  Если никакая начальная часть строки `numString` не может быть успешно преобразована в число с плавающей запятой, возвращается значение `NaN` \(не число\).  
  
```javascript  
parseFloat("abc")      // Returns NaN.  
parseFloat("1.2abc")   // Returns 1.2.  
```  
  
 Проверить результат на наличие значения `NaN` можно с помощью функции `isNaN`.  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Относится к**: [Объект Global](../../javascript/reference/global-object-javascript.md)  
  
## См. также  
 [Функция isNaN](../../javascript/reference/isnan-function-javascript.md)   
 [Функция parseInt](../../javascript/reference/parseint-function-javascript.md)   
 [Объект String](../../javascript/reference/string-object-javascript.md)