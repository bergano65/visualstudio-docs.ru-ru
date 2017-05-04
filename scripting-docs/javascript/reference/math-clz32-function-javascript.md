---
title: "Функция Math.clz32 (JavaScript) | Microsoft Docs"
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
ms.assetid: 34615d7a-6d88-4ab5-a696-7e496caa51db
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Функция Math.clz32 (JavaScript)
Возвращает число начальных нулей в 32\-разрядном двоичном представлении числа.  
  
## Синтаксис  
  
```  
  
Math.clz32(  
number  
)   
```  
  
## Заметки  
 Если значение `number` равно 0, результат будет 32.  Если самый значимый бит 32\-разрядной двоичной кодировки `number` равен 1, результат будет 0.  
  
## Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **Применимо к** [Объект Math](../../javascript/reference/math-object-javascript.md)