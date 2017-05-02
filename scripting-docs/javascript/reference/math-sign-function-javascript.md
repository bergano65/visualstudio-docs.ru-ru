---
title: "Функция Math.sign (JavaScript) | Microsoft Docs"
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
ms.assetid: 8b462020-ceff-4947-8dd1-c78e6aff8d98
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Функция Math.sign (JavaScript)
Возвращает знак числа, указывающий, является ли число положительным, отрицательным или равным 0.  
  
## Синтаксис  
  
```  
Math.sign(number)  
```  
  
## Заметки  
 Обязательный аргумент `number` является числовым выражением, для которого требуется знак.  
  
 Возвращается одно из следующих значений:  
  
-   `NaN`, если `number` равно `NaN`.  
  
-   −0, если `number` равно −0.  
  
-   \+0, если `number` равно \+0.  
  
-   −1, если `number` является отрицательным числом и не равно −0.  
  
-   \+1, если `number` является положительным числом и не равно \+0.  
  
## Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]