---
title: "Метод startsWith (String) (JavaScript) | Microsoft Docs"
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
ms.assetid: 871def4a-0f96-4675-b6ff-2349f4996511
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Метод startsWith (String) (JavaScript)
Возвращает значение, показывающее, начинается ли строка или подстрока с другой указанной строки.  
  
## Синтаксис  
  
```vb  
  
stringObj.startsWith(str, [, position]);  
```  
  
#### Параметры  
 `stringObj`  
 Обязательный.  Объект string для поиска.  
  
 `str`  
 Обязательный.  Строка поиска.  
  
 `position`  
 Необязательный.  Позиция первого символа для поиска в объекте string, начинающемся с 0.  
  
## Возвращаемое значение  
 Если строка в позиции `position` начинается с искомой строки, метод `startsWith` возвращает значение `true`; в противном случае возвращается значение `false`.  
  
## Исключения  
 Если `str` представляет собой `RegExp`, возникает ошибка `TypeError`.  
  
## Заметки  
  
## Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]