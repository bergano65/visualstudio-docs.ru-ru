---
title: "Метод substr (String) (JavaScript) | Microsoft Docs"
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
  - "substr"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "substr - метод"
ms.assetid: f12541c1-2623-482e-941d-2e22bc3c4a4a
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Метод substr (String) (JavaScript)
Получает подстроку указанной длины, которая начинается с указанной позиции.  
  
## Синтаксис  
  
```  
  
stringvar.substr(start [, length ])   
```  
  
## Параметры  
 `stringvar`  
 Обязательный.  Строковый литерал или объект `String`, из которого извлекается подстрока.  
  
 `start`  
 Обязательный.  Начальная позиция требуемой подстроки.  Индекс первого знака строки равен нулю.  
  
 `length`  
 Необязательный.  Число знаков, которые следует включить в возвращаемую подстроку.  
  
## Заметки  
 Если значение `length` равно нулю или является отрицательным, возвращается пустая строка.  Если этот аргумент не указан, подстрока продолжается до конца `stringvar`.  
  
## Пример  
 В следующем примере показано использование метода `substr`.  
  
```javascript  
var s = "The quick brown fox jumps over the lazy dog.";  
var ss = s.substr(10, 5);    
document.write("[" + ss + "] <br>");  
  
ss = s.substr(10);  
document.write("[" + ss + "] <br>");  
  
ss = s.substr(10, -5);  
document.write("[" + ss + "] <br>");  
  
// Output:  
// [brown]   
// [brown fox jumps over the lazy dog.]   
// []  
```  
  
## Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Относится к**: [Объект String](../../javascript/reference/string-object-javascript.md)  
  
## См. также  
 [Метод substring \(String\)](../../javascript/reference/substring-method-string-javascript.md)