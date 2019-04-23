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
ms.openlocfilehash: 4442143b2766ed3608a852d0f811a6b943fd19df
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60117061"
---
# <a name="function-expected"></a>Требуется функция
Либо была предпринята попытка вызвать один из **прототип функции** методов на объекте, который не был `Function` объекта или использовать объект в контексте вызова функции. Например, следующий код создает эту ошибку, так как **пример** не является функцией.  
  
```JavaScript  
var example = new Object();  // Create a new object called "example".  
var x = example();           // Try and call example as if it were a function.  
```  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Вызывать только **прототип функции** методы `Function` объектов.  
  
- Убедитесь, что используется оператор вызова функции `()` вызывать только функции.  
  
## <a name="see-also"></a>См. также  
 [Объект функции](../../javascript/reference/function-object-javascript.md)   
 [Свойство prototype (Object)](../../javascript/reference/prototype-property-object-javascript.md)