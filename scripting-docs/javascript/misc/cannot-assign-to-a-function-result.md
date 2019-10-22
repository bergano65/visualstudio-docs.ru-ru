---
title: Невозможно присвоить результат функции | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: aca09fe3b516fbb8f27def982bf34a22d33d4ada
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572359"
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
  
## <a name="see-also"></a>См. также  
 [Объект функции](../../javascript/reference/function-object-javascript.md)    
 [Написание кода JavaScript](../../javascript/writing-javascript-code.md)    
 [Функции](../../javascript/functions-javascript.md)