---
title: "Ожидалась функция | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5002
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f62ade94-9f6f-4832-9b9b-49a06a385bbe
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aa2db3e95d4baece288c9f984a7a9cf7a82c9d1d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="function-expected"></a>Ожидалась функция
Либо предпринята попытка вызвать один из **прототип функции** методов на объекте, который не был `Function` объекта, или использовать объект в контексте вызова функции. Например, приведенный ниже код вызывает эту ошибку, так как **пример** не является функцией.  
  
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