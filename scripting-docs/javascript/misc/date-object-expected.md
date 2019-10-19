---
title: Ожидался объект даты | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5006
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: d6ab82e6-ca64-46b4-a06c-5c6b0aa057cb
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 10af48c4804df3b5513df71578b948abe73ff8c2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572899"
---
# <a name="date-object-expected"></a>Ожидается объект даты
Предпринята попытка вызвать метод **Date. prototype. ToString** или **Date. prototype. valueOf** для объекта типа, отличного от `Date`. Объект этого типа вызова должен иметь тип `Date`. Пример:  
  
```JavaScript  
var o = new Object;  
o.f = Date.prototype.toString;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Вызываются только методы **Date. prototype. ToString** или **Date. prototype. valueOf** для объектов типа `Date`.  
  
## <a name="see-also"></a>См. также  
 [Объект Date](../../javascript/reference/date-object-javascript.md)   
 [метод GETDATE (Date)](../../javascript/reference/getdate-method-date-javascript.md)    
 [Встроенные объекты](../../javascript/intrinsic-objects-javascript.md)