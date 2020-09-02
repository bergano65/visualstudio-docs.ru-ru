---
title: Циклическая ссылка в аргументе значения не поддерживается | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 633ed9c37e8ccde0844205910a8fa2dc12d91414
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85817623"
---
# <a name="circular-reference-in-value-argument-not-supported"></a>Циклическая ссылка в аргументе значения не поддерживается
Предпринята попытка вызова `JSON.stringify` со значением, которое является недопустимым. `value`Аргумент, массив или объект, содержит циклическую ссылку.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Удалите циклическую ссылку из аргумента.  
  
## <a name="example"></a>Пример  
 Код в этом примере вызывает ошибку времени выполнения, так как `john` имеет ссылку на `mary` и `mary` имеет ссылку на `john` . чтобы удалить циклическую ссылку, удалите или отмените свойство `brother` `mary` объекта или `sister` свойства `john` объекта.  
  
```JavaScript  
var john = new Object();  
var mary = new Object();  
john.sister = mary;  
mary.brother = john;  
  
// This line causes a runtime error.  
var error = JSON.stringify(john);  
```  
  
## <a name="see-also"></a>См. также раздел  
 [Объект JSON](../../javascript/reference/json-object-javascript.md)   
 [Функция JSON. Parse](../../javascript/reference/json-parse-function-javascript.md)   
 [Ошибки времени выполнения JavaScript](../../javascript/reference/javascript-run-time-errors.md)