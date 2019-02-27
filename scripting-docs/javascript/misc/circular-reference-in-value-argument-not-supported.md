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
ms.openlocfilehash: 1235c8b1bb7b815b5f26e0ffb744c31a3575ba81
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/26/2019
ms.locfileid: "56841095"
---
# <a name="circular-reference-in-value-argument-not-supported"></a>Циклическая ссылка в аргументе значения не поддерживается
Предпринята попытка вызвать `JSON.stringify` со значением, которое является недопустимым. `value` Аргументов, массив или объект, содержит циклическую ссылку.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Удалите циклическую ссылку из аргумента.  
  
## <a name="example"></a>Пример  
 В данном примере кода приводит к ошибке времени выполнения, поскольку `john` содержит ссылку на `mary` и `mary` содержит ссылку на `john`. Чтобы удалить циклическую ссылку, либо удалите или свойство `brother` из `mary` объекта или `sister` свойства из `john` объекта.  
  
```JavaScript  
var john = new Object();  
var mary = new Object();  
john.sister = mary;  
mary.brother = john;  
  
// This line causes a runtime error.  
var error = JSON.stringify(john);  
```  
  
## <a name="see-also"></a>См. также  
 [Объект JSON](../../javascript/reference/json-object-javascript.md)   
 [Функция JSON.parse](../../javascript/reference/json-parse-function-javascript.md)   
 [Ошибки времени выполнения JavaScript](../../javascript/reference/javascript-run-time-errors.md)