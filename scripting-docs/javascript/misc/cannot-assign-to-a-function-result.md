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
ms.openlocfilehash: 226056f139e45f432d757aff8f8774b013742de3
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60076816"
---
# <a name="cannot-assign-to-a-function-result"></a>Присвоение результату функции невозможно
Предпринята попытка присвоить значение результату функции. Результат функции может быть присвоен переменной, но он не может использоваться в качестве переменной. Если вы хотите присвоить новое значение к самой функции, опустите скобки (оператор вызова функции). Ниже приведен пример ситуации, в котором возникает эта ошибка.  
  
```js
myFunction() = 42;  // Attempting to assign the value 42 to the result of the function call.  
```  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Не используйте значение результат вызова функции как что-нибудь, вы можете *назначить*. Можно назначить результат вызова функции *переменной* на то, что.  
  
    ```JavaScript  
    myVar = myFunction(42);  
    ```  
  
- Кроме того можно назначить функция сам (а не его возвращаемое значение) переменной.  
  
    ```JavaScript  
    myFunction = new Function("return 42;");  
    ```  
  
## <a name="see-also"></a>См. также  
 [Объект функции](../../javascript/reference/function-object-javascript.md)   
 [Написание кода JavaScript](../../javascript/writing-javascript-code.md)   
 [Функции](../../javascript/functions-javascript.md)