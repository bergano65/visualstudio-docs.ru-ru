---
title: Ожидалась функция | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5002
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f62ade94-9f6f-4832-9b9b-49a06a385bbe
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 41d1ecc982dcdc4d494fc167e4784e9121bec15e
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/26/2019
ms.locfileid: "56843939"
---
# <a name="function-expected"></a>Требуется функция
Либо была предпринята попытка вызвать один из **прототип функции** методов на объекте, который не был `Function` объекта или использовать объект в контексте вызова функции. Например, следующий код создает эту ошибку, так как **пример** не является функцией.  
  
```JavaScript  
var example = new Object();  // Create a new object called "example".  
var x = example();           // Try and call example as if it were a function.  
```  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Вызывать только **прототип функции** методы `Function` объектов.  
  
-   Убедитесь, что используется оператор вызова функции `()` вызывать только функции.  
  
## <a name="see-also"></a>См. также  
 [Объект функции](../../javascript/reference/function-object-javascript.md)   
 [Свойство prototype (Object)](../../javascript/reference/prototype-property-object-javascript.md)