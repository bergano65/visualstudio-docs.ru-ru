---
title: "Свойство stack (Error) (JavaScript) | Microsoft Docs"
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
  - "Error.stack"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "стек ошибок [JavaScript]"
  - "JavaScript: стек ошибок"
ms.assetid: 1dc21fdd-853c-4664-bf1c-24eb1f6f2daf
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Свойство stack (Error) (JavaScript)
Получает или задает стек ошибок в качестве строки, содержащей кадры трассировки стека.  
  
## Синтаксис  
  
```  
  
object  
.stack   
```  
  
## Заметки  
 Свойству `stack` задается значение `undefined`, если ошибка сконструирована, и свойство получает сведения о трассировке при возникновении ошибки.  Если ошибка возникает несколько раз, то значение свойства `stack` обновляется каждый раз при ее возникновении.  
  
 Кадры стека отображаются в следующем формате: в FunctionName \(\<полное имя или URL\-адрес\>: \<номер строки\>:\< номер столбца\>\)  
  
 При создании собственного объекта Error и присвоении значения трассировке стека это значение не будет перезаписано при возникновении ошибки.  
  
 Свойство `stack` не отображает встраиваемые функции в кадрах.  Оно показывает только физические стеки.  
  
## Пример  
 В следующем примере показано, как получить стек при перехвате ошибки.  
  
```javascript  
try  
    {  
        var x = y.name;  
    }  
catch(e)  
    {  
        document.write ("Error stack: ")  
        document.write (e.stack);  
    }  
```  
  
## Пример  
 В следующем примере показано, как задать, а затем получить стек.  
  
```javascript  
try  
    {  
        var err = Error("my error");  
        err.stack = "my stack trace";  
        throw err;  
    }  
catch(e)  
    {  
        document.write ("Error stack: ")  
        document.write (e.stack);  
    }  
```  
  
## Требования  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]  
  
 **Применяется к**: [Объект Error](../../javascript/reference/error-object-javascript.md)  
  
## См. также  
 [Свойство description \(Error\)](../../javascript/reference/description-property-error-javascript.md)   
 [Свойство message \(Error\)](../../javascript/reference/message-property-error-javascript.md)   
 [Свойство name \(Error\)](../../javascript/reference/name-property-error-javascript.md)   
 [Свойство stackTraceLimit \(Error\)](../../javascript/reference/stacktracelimit-property-error-javascript.md)