---
title: оператор "return" за пределами функции | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 32eadcf5ae88dbe64c8ccdb3effbb85bc79f9b32
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85816739"
---
# <a name="return-statement-outside-of-function"></a>Оператор return за пределами функции
Вы использовали `return` инструкцию в глобальной области кода. `return`Оператор должен находиться только в теле функции.  
  
 Вызов функции с помощью `()` оператора является выражением. Все выражения имеют значения; `return`оператор используется для указания значения, возвращаемого функцией. Общая форма:  
  
```js
  
return [ expression ];  
```  
  
 При `return` выполнении инструкции *выражение* вычисляется и возвращается в качестве значения функции. Если выражение отсутствует, возвращается значение **undefine** .  
  
 Выполнение функции прекращается при `return` выполнении инструкции, даже если в теле функции остались другие инструкции. Исключением из этого правила является ситуация, когда оператор **return** встречается в блоке **try** и имеется соответствующий блок **finally** . код в блоке **finally** будет выполнен до возвращения функции.  
  
 Если функция возвращает значение, поскольку достигает конца тела функции без выполнения `return` инструкции, возвращается значение **undefine** (это означает, что результат функции не может использоваться как часть выражения большего размера).  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Удалите `return` оператор из основного текста кода (глобальной области).  
  
## <a name="see-also"></a>См. также  
 [Оператор Return](../../javascript/reference/return-statement-javascript.md)   
 [Объект функции](../../javascript/reference/function-object-javascript.md)   
 [Свойство caller (Function)](../../javascript/reference/caller-property-function-javascript.md)