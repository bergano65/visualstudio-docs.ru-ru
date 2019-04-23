---
title: оператор за пределами функции «return» | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 03568f9f-5f4f-4a10-a738-9a73f3832b9e
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 01ef96385d5fe3dccf14a7491e67983d39913280
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60100395"
---
# <a name="return-statement-outside-of-function"></a>Оператор return за пределами функции
Вы использовали `return` оператор в глобальной области кода. `return` Оператор должен отображаться только в теле функции.  
  
 Вызов функции с помощью `()` оператор — это выражение. Все выражения имеют значения; `return` оператор используется для указания значения, возвращаемого функцией. Выглядит следующим образом:  
  
```js
  
return [ expression ];  
```  
  
 Когда `return` выполняется инструкция, *выражение* вычисляется и возвращается в качестве значения функции. Если отсутствует выражение, **неопределенный** возвращается.  
  
 Выполнение функции останавливается, когда `return` инструкция выполняется, даже при наличии других инструкций, по-прежнему осталось в теле функции. Исключением из этого правила является Если **возвращают** оператор находится внутри **попробуйте** блока, и есть соответствующая **наконец** блока, код в  **Наконец** блок будет выполняться до выполнения возврата функцией.  
  
 Если функция возвращает, так как она достигает конца тела функции без выполнения `return` инструкции, возвращаемое значение **неопределенный** значение (это означает, что результатом функции не может использоваться как часть более крупного выражения ).  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Удалить `return` инструкции от основной части кода (глобальная область).  
  
## <a name="see-also"></a>См. также  
 [Оператор return](../../javascript/reference/return-statement-javascript.md)   
 [Объект функции](../../javascript/reference/function-object-javascript.md)   
 [Свойство caller (Function)](../../javascript/reference/caller-property-function-javascript.md)