---
title: "Метод split (String) (JavaScript) | Microsoft Docs"
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
  - "split"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "split - метод"
ms.assetid: 7f093336-c887-4efb-b91f-819b6d18a181
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Метод split (String) (JavaScript)
Разбивает строку на подстроки, используя заданный разделитель, и возвращает их в виде массива.  
  
## Синтаксис  
  
```  
  
stringObj.split([separator[, limit]])  
```  
  
## Параметры  
 `stringObj`  
 Обязательный.  Объект `String` или строковый литерал, который необходимо разделить.  Этот объект не изменяется методом **split**.  
  
 `separator`  
 Необязательный.  Строка или объект **Regular Expression**, задающая один или несколько знаков, используемых при разделении строк.  Если этот параметр не указан, возвращается одноэлементный массив, содержащий всю строку.  
  
 `limit`  
 Необязательный.  Значение, ограничивающее число элементов, возвращаемых в массиве.  
  
## Возвращаемое значение  
 Результатом применения метода **split** является массив строк, разделенных там, где в строке `stringObj` встречается `separator`.  Аргумент `separator` не возвращается как часть какого\-либо элемента массива.  
  
## Пример  
 В следующем примере показано использование метода **split**.  
  
```javascript  
var s = "The quick brown fox jumps over the lazy dog.";  
var ss = s.split(" ");  
for (var i in ss) {  
    document.write(ss[i]);  
    document.write("<br/>");  
}  
  
// Output:   
// The  
// quick  
// brown  
// fox  
// jumps  
// over  
// the  
// lazy  
// dog.  
  
```  
  
## Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Применение**: [Объект String](../../javascript/reference/string-object-javascript.md)  
  
## См. также  
 [Метод concat \(строка\)](../../javascript/reference/concat-method-string-javascript.md)   
 [Объект RegExp](../../javascript/reference/regexp-object-javascript.md)   
 [Объект Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/ru-ru/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [Пример приложения с функциями прокрутки, сдвига и масштабирования](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)