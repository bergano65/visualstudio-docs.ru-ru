---
title: "Функция Debug.write (JavaScript) | Microsoft Docs"
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
  - "Write"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "write - метод[JavaScript]"
ms.assetid: fd1cfbb3-46cb-47cc-896c-a70d457dd413
caps.latest.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 22
---
# Функция Debug.write (JavaScript)
Отправляет строки в отладчик скриптов.  
  
## Синтаксис  
  
```  
  
Debug.write([str1 [, str2 [, ... [, strN]]]])  
```  
  
## Параметры  
 *str1, str2, ... , strN*  
 Необязательный.  Строки, которые требуется отправить в отладчик скриптов.  
  
## Заметки  
 Функция `Debug.write` отправляет строки в окно интерпретации отладчика скриптов во время выполнения.  Если не выполняется отладка скрипта, функция `Debug.write` не имеет никакого действия.  
  
 Функция `Debug.write` практически идентична функции `Debug.writeln`.  Единственное отличие заключается в том, что функция `Debug.writeln` отправляет символ новой строки после отправки строк.  
  
## Пример  
 В этом примере функция `Debug.write` используется для отображения значения переменной в окне интерпретации отладчика скриптов.  
  
> [!NOTE]
>  Для выполнения этого примера необходимо, чтобы был установлен отладчик скриптов и скрипт выполнялся в режиме отладки.  
>   
>  Браузер Internet Explorer 8 включает в себя отладчик [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  При использовании более ранней версии Internet Explorer см. раздел [Практическое руководство. Включение и запуск отладки сценариев из Internet Explorer](http://go.microsoft.com/fwlink/?LinkId=133801).  
  
```javascript  
var counter = 42;  
Debug.write("The value of counter is " + counter);  
```  
  
## Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Относится к**: [Объект Debug](../../javascript/reference/debug-object-javascript.md)  
  
## См. также  
 [Функция Debug.writeln](../../javascript/reference/debug-writeln-function-javascript.md)