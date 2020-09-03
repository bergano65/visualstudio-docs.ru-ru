---
title: Невозможно присвоить результат функции | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5003
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ee8ffb3a-1451-4cb3-99bf-5e9cf8b77d79
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 84ec3426c80da0578dda7cb99e9160b81e31ab87
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85817636"
---
# <a name="cannot-assign-to-a-function-result"></a>Присвоение результату функции невозможно
Предпринята попытка присвоить значение результату функции. Результат функции можно присвоить переменной, но нельзя использовать в качестве переменной. Если необходимо назначить новое значение самой функции, не указывайте круглые скобки (оператор вызова функции). В следующем примере показана ситуация, в которой возникает эта ошибка.  
  
```js
myFunction() = 42;  // Attempting to assign the value 42 to the result of the function call.  
```  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Не используйте значение результата вызова функции, как и то, которое можно *присвоить*. Вы можете присвоить результат вызова функции *переменной* .  
  
    ```JavaScript  
    myVar = myFunction(42);  
    ```  
  
- Кроме того, в переменную можно назначить саму функцию (а не ее возвращаемое значение).  
  
    ```JavaScript  
    myFunction = new Function("return 42;");  
    ```  
  
## <a name="see-also"></a>См. также раздел  
 [Объект функции](../../javascript/reference/function-object-javascript.md)   
 [Написание кода JavaScript](../../javascript/writing-javascript-code.md)   
 [Функции](../../javascript/functions-javascript.md)