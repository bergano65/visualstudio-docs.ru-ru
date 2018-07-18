---
title: '&#39; возврата &#39; Инструкция за пределами функции | Документы Microsoft'
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
- VS.WebClient.Help.SCRIPT1018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 03568f9f-5f4f-4a10-a738-9a73f3832b9e
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07b633c87dc11b291a5a5783f8121b2a368996d6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633514"
---
# <a name="39return39-statement-outside-of-function"></a>&#39; возврата &#39; Инструкция за пределами функции
Вы использовали `return` оператор в глобальной области кода. `return` Оператор может находиться только в теле функции.  
  
 Вызов функции с `()` оператор — это выражение. Все выражения имеют значения; `return` оператор используется для указания значения, возвращенного функцией. Выглядит следующим образом:  
  
```  
  
return [ expression ];  
```  
  
 Когда `return` выполняется инструкция, *выражение* вычисляется и возвращается в качестве значения функции. Если выражение не **не определено** возвращается.  
  
 Останавливает выполнение функции, когда `return` инструкция выполняется, даже если существуют другие инструкции, которые остались в теле функции. Исключение из этого правила — если **возвращают** оператор находится внутри **повторите** блока, и имеется соответствующий **наконец** блок кода  **Наконец** блок будет выполняться до выполнения возврата функцией.  
  
 Если функция возвращает в результате достижения конца тела функции без выполнения `return` инструкции, возвращаемое значение **не определено** (это означает результат функции не может использоваться в рамках более крупного выражения ).  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Удалить `return` инструкции от основной части кода (глобальная область).  
  
## <a name="see-also"></a>См. также  
 [Оператор return](../../javascript/reference/return-statement-javascript.md)   
 [Объект функции](../../javascript/reference/function-object-javascript.md)   
 [Свойство caller (Function)](../../javascript/reference/caller-property-function-javascript.md)