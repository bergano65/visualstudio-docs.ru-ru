---
title: "Свойство number (Error) (JavaScript) | Microsoft Docs"
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
  - "Number"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Number - свойство"
ms.assetid: 8697e20b-a2b0-4e26-85c0-ab07ddfe8281
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# Свойство number (Error) (JavaScript)
Возвращает или задает числовое значение, связанное с определенной ошибкой.  Объект `Error` имеет свойство по умолчанию **number**.  
  
## Синтаксис  
  
```  
  
object  
.number [= errorNumber]  
```  
  
## Параметры  
 *Object*  
 Любой экземпляр объекта `Error`.  
  
 *errorNumber*  
 Целое число, представляющее ошибку.  
  
## Заметки  
 Номер ошибки представляет собой 32\-разрядное значение.  Старшие 16 разрядов — это код устройства, а младшие разряды — код ошибки.  Чтобы определить код ошибки, необходимо с помощью оператора `&` \(побитового И\) объединить свойство number с шестнадцатеричным числом `0xFFFF`.  
  
## Пример  
 В следующем примере создается исключение и отображается код ошибки, полученный на основании номера ошибки.  
  
```javascript  
try  
    {  
    // Cause an error.  
    var x = y;  
    }  
catch(e)  
    {  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF)  
    document.write ("<br />");  
  
    document.write ("Facility Code: ")  
    document.write(e.number>>16 & 0x1FFF)  
    document.write ("<br />");  
  
    document.write ("Error Message: ")  
    document.write (e.message)  
    }  
```  
  
## Пример  
 Результат выполнения этого кода следующий.  
  
```javascript  
Error Code: 5009  
Facility Code: 10  
Error Message: 'y' is undefined  
```  
  
## Требования  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
 **Относится к**: [Объект Error](../../javascript/reference/error-object-javascript.md)  
  
## См. также  
 [Свойство description \(Error\)](../../javascript/reference/description-property-error-javascript.md)   
 [Свойство message \(Error\)](../../javascript/reference/message-property-error-javascript.md)   
 [Свойство name \(Error\)](../../javascript/reference/name-property-error-javascript.md)