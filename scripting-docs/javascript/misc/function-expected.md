---
title: Требуется функция | Документация Майкрософт
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
ms.openlocfilehash: 988ca00613d3dec4c55309fd77bc43705a6038ae
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576583"
---
# <a name="function-expected"></a>Требуется функция
Либо вы попытались вызвать один из методов **прототипа функции** для объекта, который не является `Function`ным объектом, либо вы использовали объект в контексте вызова функции. Например, следующий код выдает эту ошибку, так как **Пример** не является функцией.  
  
```JavaScript  
var example = new Object();  // Create a new object called "example".  
var x = example();           // Try and call example as if it were a function.  
```  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Вызываются только методы **прототипа функции** для `Function`ных объектов.  
  
- Убедитесь, что для вызова функций используется оператор вызова функции `()`.  
  
## <a name="see-also"></a>См. также  
 [Объект функции](../../javascript/reference/function-object-javascript.md)    
 [Свойство prototype (Object)](../../javascript/reference/prototype-property-object-javascript.md)