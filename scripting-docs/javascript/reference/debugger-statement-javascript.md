---
title: "Оператор debugger (JavaScript) | Microsoft Docs"
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
  - "debugger_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "debugger - оператор"
ms.assetid: c6d2e193-c1f7-4fb3-8a4e-cc9823174ae4
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Оператор debugger (JavaScript)
Приостанавливает выполнение.  
  
## Синтаксис  
  
```  
debugger  
```  
  
## Заметки  
 Операторы `debugger` можно размещать в любом месте процедур для приостановки выполнения.  Использование оператора `debugger` аналогично установке точки останова в коде.  
  
 Оператор `debugger` приостанавливает выполнение, но не закрывает никакие файлы и не очищает никакие переменных.  
  
> [!NOTE]
>  Если не выполняется отладка скрипта, оператор `debugger` не имеет никакого действия.  
  
## Пример  
 В данном примере оператор `debugger` используется для приостановки выполнения на каждом шаге цикла `for`.  
  
> [!NOTE]
>  Для выполнения этого примера необходимо, чтобы был установлен отладчик скриптов и скрипт выполнялся в режиме отладки.  
>   
>  Браузер Internet Explorer 8 включает в себя отладчик [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  При использовании более ранней версии Internet Explorer см. раздел [Практическое руководство. Включение и запуск отладки сценариев из Internet Explorer](http://go.microsoft.com/fwlink/?LinkId=133801).  
  
```javascript  
for(i = 1; i<5; i++) {  
   // Print i to the Output window.  
   Debug.write("loop index is " + i);  
   // Wait for user to resume.  
   debugger  
}  
```  
  
## Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## См. также  
 [Операторы JavaScript](../../javascript/reference/javascript-statements.md)   
 [Условная компиляция](../../javascript/advanced/conditional-compilation-javascript.md)