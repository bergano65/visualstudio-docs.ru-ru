---
title: Недопустимый аргумент замены | Документация Майкрософт
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
- VS.WebClient.Help.SCRIPT5035
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 4727186f-facd-4aa6-9447-bbefbae83f07
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0f144e733bf115cc98bf61b23a2ed3e4e3cda1e0
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2019
ms.locfileid: "54346219"
---
# <a name="invalid-replacer-argument"></a>Недопустимый аргумент замены
Предпринята попытка вызвать `JSON.stringify` с аргументом, который является недопустимым. `replacer` Аргумент должен быть функцией или массивом.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Изменение `replacer` аргумент к функции или массив.  
  
## <a name="example"></a>Пример  
 В данном примере кода приводит к ошибке времени выполнения, поскольку `memberfilter` — это объект, а не функция или массив.  
  
```JavaScript  
var contact = new Object();  
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
var memberfilter = new Object();  
  
// This line will cause a runtime error.  
var jsontext = JSON.stringify(contact, memberfilter, "\t");  
```  
  
## <a name="see-also"></a>См. также  
 [Объект JSON](../../javascript/reference/json-object-javascript.md)   
 [Функция JSON.parse](../../javascript/reference/json-parse-function-javascript.md)   
 [Ошибки времени выполнения JavaScript](../../javascript/reference/javascript-run-time-errors.md)