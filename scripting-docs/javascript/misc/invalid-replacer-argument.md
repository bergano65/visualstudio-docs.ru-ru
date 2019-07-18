---
title: Недопустимый аргумент замены | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 46e01a4e6bb989fad2da6f979c79b7aba13df63a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63007318"
---
# <a name="invalid-replacer-argument"></a>Недопустимый аргумент замены
Предпринята попытка вызвать `JSON.stringify` с аргументом, который является недопустимым. `replacer` Аргумент должен быть функцией или массивом.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Изменение `replacer` аргумент к функции или массив.  
  
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