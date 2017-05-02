---
title: "Свойство stackTraceLimit (Error) (JavaScript) | Microsoft Docs"
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
  - "Error.stackTraceLimit"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "лимит отслеживания стека ошибок [JavaScript]"
  - "JavaScript: стек ошибок"
  - "стек ошибок [JavaScript]"
  - "JavaScript: лимит трассировки стека"
ms.assetid: 127ef8e8-892e-4263-9ebc-03364af01212
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Свойство stackTraceLimit (Error) (JavaScript)
Возвращает или задает ограничение трассировки стека, которое равно числу кадров ошибки для отображения.  Ограничение по умолчанию равно 10.  
  
## Синтаксис  
  
```  
  
Error  
.stackTraceLimit   
```  
  
## Заметки  
 Можно задать свойство `stackTraceLimit` равным любому положительному числу между 0 и `Infinity`.  Если свойство `stackTraceLimit` имеет значение 0 в момент возникновения ошибки, то стек трассировки не отображается.  Если свойство имеет отрицательное или нечисловое значение, то это значение преобразуется к 0.  Если stackTraceLimit имеет значение `Infinity`, то отображается весь стек.  В противном случае `ToUint32` используется для преобразования значения.  
  
## Пример  
 В следующем примере показано, как задать и затем получить ограничение трассировки стека.  
  
```javascript  
try  
    {  
    var err = new Error("my error");  
    Error.stackTraceLimit = 7;  
    throw err;  
    }  
catch(e)  
    {  
    document.write ("Error stack trace limit: ")  
    document.write (Error.stackTraceLimit);  
    }  
```  
  
## Требования  
 Поддерживается в Internet Explorer 10 и в приложениях [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  
  
 **Применение**: [Объект Error](../../javascript/reference/error-object-javascript.md)  
  
## См. также  
 [Свойство description \(Error\)](../../javascript/reference/description-property-error-javascript.md)   
 [Свойство message \(Error\)](../../javascript/reference/message-property-error-javascript.md)   
 [Свойство name \(Error\)](../../javascript/reference/name-property-error-javascript.md)   
 [Свойство stack \(Error\)](../../javascript/reference/stack-property-error-javascript.md)