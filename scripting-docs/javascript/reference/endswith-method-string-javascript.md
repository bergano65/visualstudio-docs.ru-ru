---
title: "Метод endsWith (String) (JavaScript) | Microsoft Docs"
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
ms.assetid: c7d836e3-bc43-4d1b-be60-0a93beb8b7a2
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Метод endsWith (String) (JavaScript)
Возвращает значение, показывающее, заканчивается ли строка или подстрока другой указанной строкой.  
  
## Синтаксис  
  
```vb  
  
stringObj.endsWith(str, [, position]);  
```  
  
#### Параметры  
 `stringObj`  
 Обязательный.  Объект string для поиска.  
  
 `str`  
 Обязательный.  Строка поиска.  
  
 `position`  
 Необязательный.  Позиция первого символа для поиска в объекте string, начинающемся с 0.  
  
## Возвращаемое значение  
 Если строка в позиции `position` заканчивается искомой строкой, метод `endsWith` возвращает значение `true`; в противном случае возвращается значение `false`.  
  
## Исключения  
 Если `str` представляет собой `RegExp`, возникает ошибка `TypeError`.  
  
## Заметки  
  
## Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]