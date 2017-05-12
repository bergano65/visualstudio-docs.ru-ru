---
title: "Метод search (String) (JavaScript) | Microsoft Docs"
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
  - "search"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "search - метод"
ms.assetid: 1cae0fbc-3319-4327-ba4e-d5fa2c4a9ba0
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Метод search (String) (JavaScript)
Находит первое вхождение подстроки при поиске с использованием регулярного выражения.  
  
## Синтаксис  
  
```  
  
stringObj.search(rgExp)   
```  
  
## Параметры  
 `stringObj`  
 Обязательный.  Объект `String` или строковый литерал, в котором выполняется поиск.  
  
 `rgExp`  
 Обязательный.  Экземпляр объекта **Regular Expression**, содержащий шаблон регулярного выражения и применимые флаги.  
  
## Возвращаемое значение  
 Если совпадение найдено, метод **search** возвращает целочисленное значение, которое указывает смещение от начала строки, по которому находится первое совпадение.  Если совпадение не найдено, возвращается значение \-1.  
  
## Заметки  
 Можно также задать флаг `i`, чтобы поиск велся с учетом регистра.  
  
## Пример  
 В следующем примере кода показано использование метода **search**.  
  
```javascript  
var src = "is but a Dream within a dream";  
var re = /dream/;  
var pos = src.search(re);  
document.write(pos);  
document.write("<br/>");  
  
re = /dream/i;  
pos = src.search(re);  
document.write(pos);  
  
// Output:   
// 24   
// 9  
  
```  
  
## Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Относится к**: [Объект String](../../javascript/reference/string-object-javascript.md)  
  
## См. также  
 [Метод exec \(Regular Expression\)](../../javascript/reference/exec-method-regular-expression-javascript.md)   
 [Метод match \(String\)](../../javascript/reference/match-method-string-javascript.md)   
 [Объект Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/ru-ru/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [Метод replace \(строка\)](../../javascript/reference/replace-method-string-javascript.md)   
 [Метод test \(Regular Expression\)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Regular Expression Programming \(JavaScript\)](http://msdn.microsoft.com/ru-ru/3b62e27c-4f07-4726-a95b-6e841807bfaf)