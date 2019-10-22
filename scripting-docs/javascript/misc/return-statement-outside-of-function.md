---
title: оператор "return" за пределами функции | Документация Майкрософт
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
ms.openlocfilehash: a90af6de8e2c238e3660111b19d13c1eaf628c9e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573691"
---
# <a name="return-statement-outside-of-function"></a>Оператор return за пределами функции
Вы использовали инструкцию `return` в глобальной области кода. Оператор `return` должен находиться только в теле функции.  
  
 Вызов функции с помощью оператора `()` является выражением. Все выражения имеют значения; Оператор `return` используется для указания значения, возвращаемого функцией. Общая форма:  
  
```js
  
return [ expression ];  
```  
  
 При выполнении инструкции `return` *выражение* вычисляется и возвращается в качестве значения функции. Если выражение отсутствует, возвращается значение **undefine** .  
  
 Выполнение функции останавливается при выполнении оператора `return`, даже если в теле функции остались другие инструкции. Исключением из этого правила является ситуация, когда оператор **return** встречается в блоке **try** и имеется соответствующий блок **finally** . код в блоке **finally** будет выполнен до возвращения функции.  
  
 Если функция возвращает значение, поскольку достигает конца тела функции без выполнения `return` инструкции, возвращается значение **undefine** (это означает, что результат функции не может использоваться как часть выражения большего размера).  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Удалите оператор `return` из основного текста кода (глобальной области).  
  
## <a name="see-also"></a>См. также  
 [Оператор return](../../javascript/reference/return-statement-javascript.md)   
 [Объект функции](../../javascript/reference/function-object-javascript.md)    
 [Свойство caller (Function)](../../javascript/reference/caller-property-function-javascript.md)