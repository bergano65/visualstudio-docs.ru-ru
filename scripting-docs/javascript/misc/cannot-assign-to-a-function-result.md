---
title: "Нельзя назначить результату функции | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5003
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ee8ffb3a-1451-4cb3-99bf-5e9cf8b77d79
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f7e7ea718aa97ab7b2eb0924458826cd1eac5672
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="cannot-assign-to-a-function-result"></a>Нельзя назначить результату функции
Предпринята попытка присвоить значение результату функции. Результатом выполнения функции может быть присвоен переменной, но он не может использоваться как переменная. Если вы хотите присвоить новое значение самой функции, опустить скобки (оператор вызова функции). В следующем примере показано ситуации, в которых возникает эта ошибка.  
  
```  
myFunction() = 42;  // Attempting to assign the value 42 to the result of the function call.  
```  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Не используйте значение результат вызова функции в качестве нечто можно *назначить*. Можно назначить результат вызова функции *переменной* на то, что.  
  
    ```JavaScript  
    myVar = myFunction(42);  
    ```  
  
-   Кроме того можно назначить функции сам (а не ее возвращаемое значение) переменной.  
  
    ```JavaScript  
    myFunction = new Function("return 42;");  
    ```  
  
## <a name="see-also"></a>См. также  
 [Объект функции](../../javascript/reference/function-object-javascript.md)   
 [Написание кода JavaScript](../../javascript/writing-javascript-code.md)   
 [Функции](../../javascript/functions-javascript.md)