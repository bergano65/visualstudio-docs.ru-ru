---
title: "Ожидается логическое значение | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5010
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 35d71b7f-53fd-44c4-a7c7-b1550c65cfd4
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 600ab26f60c2196ebc682adcffcd6b24c23cd358
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="boolean-expected"></a>Ожидается логическое значение
Предпринята попытка вызвать **Boolean.prototype.toString** или **Boolean.prototype.valueOf** метода объекта типа, отличного от `Boolean`. Объект вызова этого типа должен иметь тип `Boolean`. Например:  
  
```JavaScript  
var o = new Object;  
o.f = Boolean.prototype.toString;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Вызывать только логическое значение**. prototype.toString** или **Boolean.prototype.valueOf** методов для объектов типа **типа Boolean.**  
  
## <a name="see-also"></a>См. также  
 [Объект Boolean](../../javascript/reference/boolean-object-javascript.md)   
 [Типы данных](../../javascript/data-types-javascript.md)   
 [Управление выполнением программы](../../javascript/controlling-program-flow-javascript.md)   
 [Копирование, передача и сравнение данных](../../javascript/advanced/copying-passing-and-comparing-data-javascript.md)