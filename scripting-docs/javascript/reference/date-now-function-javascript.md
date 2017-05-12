---
title: "Функция Date.now (JavaScript) | Microsoft Docs"
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
  - "now - метод"
ms.assetid: 41beda89-1a40-4fb1-88b0-38c090af739b
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Функция Date.now (JavaScript)
Получает текущие дату и время  
  
## Синтаксис  
  
```  
  
Date.now()  
```  
  
## Возвращаемое значение  
 Количество миллисекунд между полуночью 1 января 1970 и текущей датой и временем.  
  
## Заметки  
 [Метод getTime](../../javascript/reference/gettime-method-date-javascript.md) отображает количество миллисекунд между 1 января 1970 и указанной датой.  
  
 Сведения о способах подсчета затраченного времени и сравнении дат см. в разделе [Вычисление даты и времени \(JavaScript\)](../../javascript/calculating-dates-and-times-javascript.md).  
  
## Пример  
 В следующем примере показано использование метода `now`.  
  
```javascript  
var start = Date.now();  
var response = prompt("What is your name?", "");  
var end = Date.now();  
var elapsed = (end - start) / 1000;  
document.write("You took " + elapsed + " seconds" + " to type: " + response);  
  
// Output:  
// You took <seconds> seconds to type: <name>  
```  
  
## Требования  
 Не поддерживается в установленных версиях, более ранних чем Internet Explorer 9.  Однако, поддерживается в следующих режимах документов: "случайный" режим, стандартный режим Internet Explorer 6, стандартный режим Internet Explorer 7, стандартный режим Internet Explorer 8, стандартный режим Internet Explorer 9, стандартный режим Internet Explorer 10.  Также поддерживается в приложениях [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  
  
## См. также  
 [Метод getTime \(Date\)](../../javascript/reference/gettime-method-date-javascript.md)   
 [Объект Date](../../javascript/reference/date-object-javascript.md)   
 [Вычисление даты и времени \(JavaScript\)](../../javascript/calculating-dates-and-times-javascript.md)   
 [Методы JavaScript](../../javascript/reference/javascript-methods.md)