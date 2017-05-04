---
title: "Метод indexOf (строка) (JavaScript) | Microsoft Docs"
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
  - "indexOf"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "indexOf - метод, строка"
  - "строка, indexOf - метод"
ms.assetid: a17372fa-669b-471b-9240-46927a265152
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# Метод indexOf (строка) (JavaScript)
Возвращает позицию первого вхождения подстроки.  
  
## Синтаксис  
  
```  
  
strObj. indexOf(subString[, startIndex])  
```  
  
## Параметры  
 `strObj`  
 Обязательный.  Объект `String` или строковый литерал.  
  
 `subString`  
 Обязательный.  Подстрока, которую необходимо найти в строке  
  
 `startIndex`  
 Необязательный.  Индекс, с которого необходимо начать поиск объекта `String`.  Если он не указан, поиск будет производиться с начала строки.  
  
## Заметки  
 Метод **indexOf** возвращает начало подстроки в объекте `String`.  Если подстрока не найдена, возвращается \-1.  
  
 Если значение `startindex` отрицательно, то `startindex` рассматривается как ноль.  Если его значение больше наибольшего индекса, он рассматривается как наибольший индекс.  
  
 Поиск выполняется слева направо.  В остальном этот метод идентичен методу **lastIndexOf**.  
  
## Пример  
 В следующем примере показано использование метода **indexOf**.  
  
```javascript  
var str = "original equipment manufacturer";  
  
var s = "equip is at position " + str.indexOf("equip");  
s += "<br />";  
s += "abc is at position " + str.indexOf("abc");  
  
document.write(s);  
  
// Output:  
// equip is at position 9  
// abc is at position -1  
```  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Применение**: [Объект String](../../javascript/reference/string-object-javascript.md)  
  
## См. также  
 [Метод lastIndexOf \(строка\)](../../javascript/reference/lastindexof-method-string-javascript.md)   
 [Пример приложения с функциями прокрутки, сдвига и масштабирования](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)