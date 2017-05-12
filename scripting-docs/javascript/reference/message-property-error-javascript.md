---
title: "Свойство message (Error) (JavaScript) | Microsoft Docs"
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
  - "message"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Message - свойство"
ms.assetid: 8cab0392-e0db-4714-827c-47ab04e8b4f2
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Свойство message (Error) (JavaScript)
Возвращает строку сообщения об ошибке.  
  
## Синтаксис  
  
```  
  
errorObj.message  
```  
  
## Параметры  
 `errorObj`  
 Обязательный.  Экземпляр объекта `Error`.  
  
## Заметки  
 Свойство `message` возвращает строку, содержащую сообщение об ошибке, связанное с определенной ошибкой.  
  
 Свойства `description` и `message` предоставляют те же функциональные возможности.  Свойство `description` предоставляет обратную совместимость; свойство `message` соответствует стандарту ECMA.  
  
## Пример  
 В следующем примере создается исключение TypeError, отображаются имя ошибки и соответствующее ей сообщение.  
  
```javascript  
try  
{  
    // Cause an error.  
    var x = y;  
}  
catch(e)  
{  
    document.write ("Error Message: " + e.message);  
    document.write ("<br />");  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF)  
    document.write ("<br />");  
    document.write ("Error Name: " + e.name);  
}  
```  
  
## Пример  
 Результат выполнения этого кода следующий.  
  
```javascript  
Error Message: 'y' is undefined  
Error Code: 5009  
Error Name: TypeError  
```  
  
## Требования  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
 **Относится к**: [Объект Error](../../javascript/reference/error-object-javascript.md)  
  
## См. также  
 [Свойство description \(Error\)](../../javascript/reference/description-property-error-javascript.md)   
 [Свойство name \(Error\)](../../javascript/reference/name-property-error-javascript.md)