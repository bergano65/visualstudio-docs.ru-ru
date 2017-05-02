---
title: "Невозможно присвоить значение результату функции | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT5003"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: ee8ffb3a-1451-4cb3-99bf-5e9cf8b77d79
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Невозможно присвоить значение результату функции
Предпринята попытка присвоить значение результату функции.  Результат функции можно присвоить переменной, однако его нельзя использовать как переменную.  Чтобы присвоить новое значение самой функции, удалите скобки \(оператор вызова функции\).  В следующем примере демонстрируется ситуация, в которой возникает эта ошибка.  
  
```  
myFunction() = 42;  // Attempting to assign the value 42 to the result of the function call.  
```  
  
### Исправление ошибки  
  
-   Не используйте результат вызова функции как объект, которому можно *присвоить значение*.  Однако можно присвоить результат вызова функции *переменной*.  
  
    ```javascript  
    myVar = myFunction(42);  
    ```  
  
-   Кроме того, можно присвоить переменной саму функцию \(а не возвращаемое ею значение\).  
  
    ```javascript  
    myFunction = new Function("return 42;");  
    ```  
  
## См. также  
 [Объект Function](../../javascript/reference/function-object-javascript.md)   
 [Написание кода JavaScript](../../javascript/writing-javascript-code.md)   
 [Функции](../../javascript/functions-javascript.md)