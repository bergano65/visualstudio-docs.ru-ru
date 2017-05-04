---
title: "Метод charAt (строка) (JavaScript) | Microsoft Docs"
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
  - "charAt"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "объект String, возврат символов"
  - "charAt - метод"
  - "символы, возврат части"
ms.assetid: 63173e15-17f6-47c5-8f94-98ef1eb04c1a
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Метод charAt (строка) (JavaScript)
Возвращает символ по указанному индексу.  
  
## Синтаксис  
  
```  
  
strObj. charAt(index)  
```  
  
## Параметры  
 `strObj`  
 Обязательный.  Любой объект `String` или строковый литерал.  
  
 `index`  
 Обязательный.  Индекс требуемого знака \(начиная с нуля\).  
  
## Заметки  
 Метод `charAt` возвращает символьное значение, представляющее символ, расположенный по указанному индексу `index`.  Первый знак строки имеет индекс 0, второй — индекс 1 и т. д.  При указании значения `index`, выходящего за пределы допустимого диапазона, возвращается пустая строка.  
  
## Пример  
 В следующем примере показано использование метода `charAt`.  
  
```javascript  
var str = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";  
document.write(str.charAt(str.length - 1));  
  
// Output: Z  
  
```  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Относится к**: [Объект String](../../javascript/reference/string-object-javascript.md)  
  
## См. также  
 [Объект String](../../javascript/reference/string-object-javascript.md)