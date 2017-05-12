---
title: "Функция Debug.writeln (JavaScript) | Microsoft Docs"
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
  - "writeln"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "writeIn - метод"
ms.assetid: c3aad0cd-0486-4161-9ba6-31d672da72af
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Функция Debug.writeln (JavaScript)
Отправляет строки в отладчик скриптов, завершая их символом новой строки.  
  
## Синтаксис  
  
```  
  
Debug.writeln([str1 [, str2 [, ... [, strN]]]])  
```  
  
## Параметры  
 *str1, str2, ... , strN*  
 Необязательный.  Строки, которые требуется отправить в отладчик скриптов.  
  
## Заметки  
 Функция `Debug.writeln` отправляет строки, за которыми следует символ новой строки, в окно интерпретации отладчика скриптов Microsoft Script Debugger во время выполнения.  Если не выполняется отладка скрипта, функция `Debug.writeln` не имеет никакого действия.  
  
 Функция `Debug.writeln` практически идентична функции `Debug.write`.  Единственное отличие заключается в том, что функция `Debug.write` не отправляет символ новой строки после отправки строк.  
  
## Пример  
 В этом примере функция `Debug.writeln` используется для отображения значения переменной в окне интерпретации отладчика скриптов Microsoft Script Debugger.  
  
> [!NOTE]
>  Для выполнения этого примера необходимо, чтобы был установлен отладчик скриптов и скрипт выполнялся в режиме отладки.  
>   
>  Браузер Internet Explorer 8 включает в себя отладчик [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  При использовании более ранней версии Internet Explorer см. раздел [Практическое руководство. Включение и запуск отладки сценариев из Internet Explorer](http://go.microsoft.com/fwlink/?LinkId=133801).  
  
```javascript  
var counter = 42;  
Debug.writeln("The value of counter is " + counter);  
```  
  
## Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Относится к**: [Объект Debug](../../javascript/reference/debug-object-javascript.md)  
  
## См. также  
 [Функция Debug.write](../../javascript/reference/debug-write-function-javascript.md)