---
title: "Свойство description (Error) (JavaScript) | Microsoft Docs"
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
  - "Description"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Description - свойство"
  - "обработка ошибок, описание ошибки"
  - "ошибки, description"
ms.assetid: ea727f1e-2041-4400-965c-67e6d47a1ff0
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# Свойство description (Error) (JavaScript)
Возвращает или задает строку описания, соответствующую определенной ошибке.  
  
## Синтаксис  
  
```  
  
object  
.description [= stringExpression]  
```  
  
## Параметры  
 *object*  
 Обязательный.  Любой экземпляр объекта `Error`.  
  
 `stringExpression`  
 Необязательный.  Строковое выражение, содержащее описание ошибки.  
  
## Заметки  
 Свойство **description** содержит строку сообщения об ошибке, связанного с определенной ошибкой.  Используйте значение, содержащееся в этом свойстве, для оповещения пользователя об ошибке.  
  
 Свойства **description** и **message** выполняют одну и ту же функцию; свойство **description** обеспечивает обратную совместимость, а свойство **message** соответствует стандарту ECMA.  
  
## Пример  
 В следующем примере показано использование свойства **description**.  
  
```javascript  
try  
{  
// Cause an error:  
    x = y     
}  
catch(e)  
{  
// Prints "[object Error]":  
    document.write(e)  
    document.write (" ");  
// Prints 5009:  
    document.write((e.number & 0xFFFF))    
    document.write (" ");  
// Prints "'y' is undefined":  
    document.write(e.description);  
    document.write (" ");  
// Prints "'y' is undefined":  
    document.write(e.message)  
}  
```  
  
## Требования  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
 **Относится к**: [Объект Error](../../javascript/reference/error-object-javascript.md)  
  
## См. также  
 [Свойство number \(Error\)](../../javascript/reference/number-property-error-javascript.md)   
 [Свойство message \(Error\)](../../javascript/reference/message-property-error-javascript.md)   
 [Свойство name \(Error\)](../../javascript/reference/name-property-error-javascript.md)