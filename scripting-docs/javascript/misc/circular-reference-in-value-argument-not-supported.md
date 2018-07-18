---
title: Циклическая ссылка в аргументе значения не поддерживается | Документы Microsoft
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
ms.openlocfilehash: d25489065ceece41108a75c9d3763a95e4adb924
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633144"
---
# <a name="circular-reference-in-value-argument-not-supported"></a>Циклическая ссылка в аргументе значения не поддерживается
Предпринята попытка вызвать `JSON.stringify` со значением, которое является недопустимым. `value` Аргументов, массив или объект, содержит циклическую ссылку.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Удалите циклическую ссылку из аргумента.  
  
## <a name="example"></a>Пример  
 В данном примере кода приводит к ошибке времени выполнения, поскольку `john` содержит ссылку на `mary` и `mary` содержит ссылку на `john`. Чтобы удалить циклическую ссылку, либо удалите или не задано свойство `brother` из `mary` объекта или `sister` свойство из `john` объекта.  
  
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