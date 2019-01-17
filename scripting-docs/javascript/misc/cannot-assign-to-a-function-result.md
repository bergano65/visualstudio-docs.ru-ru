---
title: Нельзя назначить результату функции | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5003
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ee8ffb3a-1451-4cb3-99bf-5e9cf8b77d79
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1a29c3f20392dc216c0306137c0dec6b22aaa58a
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093865"
---
# <a name="cannot-assign-to-a-function-result"></a>Нельзя назначить результату функции
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