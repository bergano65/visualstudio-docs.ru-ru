---
title: "Метод trim (String) (JavaScript) | Microsoft Docs"
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
helpviewer_keywords: 
  - "trim - метод"
ms.assetid: 03d38c7e-25cd-4ede-b58e-1a10b5249bab
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Метод trim (String) (JavaScript)
Удаляет из строки начальные и конечные пробелы и символы конца строки.  
  
## Синтаксис  
  
```  
  
stringObj.trim()  
```  
  
## Параметры  
 `stringObj`  
 Обязательный.  Объект `String` или строковый литерал.  Эта строка не изменяется методом `trim`.  
  
## Возвращаемое значение  
 Исходная строка с удаленными начальными и конечными пробелами и символами конца строки.  
  
## Заметки  
 К удаляемым символам относятся пробел, символ табуляции, перевод страницы, возврат каретки и перевод строки.  Полный список символов пробелов и конца строки см. в разделе [Специальные символы](../../javascript/advanced/special-characters-javascript.md).  
  
 Пример, в котором показана реализация собственного метода обрезки, см. в разделе [Прототипы и их наследование](../../javascript/advanced/prototypes-and-prototype-inheritance.md).  
  
## Пример  
 В следующем примере показано использование метода `trim`.  
  
```javascript  
var message = "    abc def     \r\n  ";  
  
document.write("[" + message.trim() + "]");  
document.write("<br/>");  
document.write("length: " + message.trim().length);  
  
// Output:  
//  [abc def]  
//  length: 7  
```  
  
## Требования  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## См. также  
 [Специальные символы](../../javascript/advanced/special-characters-javascript.md)   
 [Объект String](../../javascript/reference/string-object-javascript.md)   
 [Пример приложения с функциями прокрутки, сдвига и масштабирования](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)