---
title: Циклическая ссылка в аргументе значения не поддерживается | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5034
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 5d06f0fa-86f5-49d1-8d50-af1759990f43
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 542fca58778a7b85b3044ce984b6ea049db12509
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572333"
---
# <a name="circular-reference-in-value-argument-not-supported"></a>Циклическая ссылка в аргументе значения не поддерживается
Предпринята попытка вызвать `JSON.stringify` с недопустимым значением. Аргумент `value`, массив или объект, содержит циклическую ссылку.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Удалите циклическую ссылку из аргумента.  
  
## <a name="example"></a>Пример  
 Код в этом примере вызывает ошибку времени выполнения, так как `john` имеет ссылку на `mary` и `mary` имеет ссылку на `john`. чтобы удалить циклическую ссылку, удалите или отмените `brother` свойства объекта `mary` или свойства `sister` из объекта `john`.  
  
```JavaScript  
var john = new Object();  
var mary = new Object();  
john.sister = mary;  
mary.brother = john;  
  
// This line causes a runtime error.  
var error = JSON.stringify(john);  
```  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [объекта JSON](../../javascript/reference/json-object-javascript.md)  
 @No__t_1 [функции JSON. Parse](../../javascript/reference/json-parse-function-javascript.md)  
 [Ошибки времени выполнения JavaScript](../../javascript/reference/javascript-run-time-errors.md)