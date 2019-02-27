---
title: Нельзя назначить результату функции | Документация Майкрософт
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
ms.openlocfilehash: 38cf04b388eaea8ad85f0399978f914feb937c0a
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/26/2019
ms.locfileid: "56844017"
---
# <a name="cannot-assign-to-a-function-result"></a>Присвоение результату функции невозможно
Предпринята попытка присвоить значение результату функции. Результат функции может быть присвоен переменной, но он не может использоваться в качестве переменной. Если вы хотите присвоить новое значение к самой функции, опустите скобки (оператор вызова функции). Ниже приведен пример ситуации, в котором возникает эта ошибка.  
  
```js
myFunction() = 42;  // Attempting to assign the value 42 to the result of the function call.  
```  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Не используйте значение результат вызова функции как что-нибудь, вы можете *назначить*. Можно назначить результат вызова функции *переменной* на то, что.  
  
    ```JavaScript  
    myVar = myFunction(42);  
    ```  
  
-   Кроме того можно назначить функция сам (а не его возвращаемое значение) переменной.  
  
    ```JavaScript  
    myFunction = new Function("return 42;");  
    ```  
  
## <a name="see-also"></a>См. также  
 [Объект функции](../../javascript/reference/function-object-javascript.md)   
 [Написание кода JavaScript](../../javascript/writing-javascript-code.md)   
 [Функции](../../javascript/functions-javascript.md)