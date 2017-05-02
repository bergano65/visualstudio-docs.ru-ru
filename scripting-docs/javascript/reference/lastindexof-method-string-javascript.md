---
title: "Метод lastIndexOf (строка) (JavaScript) | Microsoft Docs"
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
  - "lastIndexOf"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "метод lastIndexOf, строка"
  - "строка, метод lastIndexOf"
ms.assetid: 1ed36ccd-0f0b-4f16-be45-0567207670af
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Метод lastIndexOf (строка) (JavaScript)
Возвращает последнее вхождение подстроки в строке.  
  
## Синтаксис  
  
```  
  
strObj.lastIndexOf(substring[, startindex])  
```  
  
## Параметры  
 `strObj`  
 Обязательный.  Объект `String` или строковый литерал.  
  
 `substring`  
 Обязательный.  Искомая подстрока.  
  
 `startindex`  
 Необязательный.  Индекс, с которого начинается поиск.  Если индекс опущен, поиск начинается с конца строки.  
  
## Заметки  
 Метод **lastIndexOf** возвращает целочисленное значение, указывающее начало подстроки в объекте `String`.  Если подстрока не найдена, возвращается \-1.  
  
 Если значение `startindex` является отрицательным, `startindex` считается равным нулю.  Если оно больше наибольшего индекса позиции символа, оно обрабатывается как наибольший возможный индекс.  
  
 Поиск выполняется начиная с последнего символа в строке.  В остальном данный метод идентичен методу **indexOf**.  
  
 В следующем примере показано использование метода **lastIndexOf**.  
  
```javascript  
var str = "time, time";  
  
var s = "";  
s += "time is at position " + str.lastIndexOf("time");  
s += "<br />";  
s += "abc is at position " + str.lastIndexOf("abc");  
  
document.write(s);  
  
// Output:  
// time is at position 6  
// abc is at position -1  
```  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Относится к**: [Объект String](../../javascript/reference/string-object-javascript.md)  
  
## См. также  
 [Метод indexOf \(строка\)](../../javascript/reference/indexof-method-string-javascript.md)