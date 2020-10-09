---
title: Ожидался объект даты | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 28531c1ac1dc73ca2bf309d412b08d23dd17bfb8
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862639"
---
# <a name="date-object-expected"></a>Ожидается объект даты
Предпринята попытка вызвать метод **Date. prototype. ToString** или **Date. prototype. valueOf** для объекта типа, отличного от `Date` . Объект этого типа вызова должен иметь тип `Date` . Пример:  
  
```JavaScript  
var o = new Object;  
o.f = Date.prototype.toString;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Вызываются только методы **Date. prototype. ToString** или **Date. prototype. valueOf** для объектов типа `Date` .  
  
## <a name="see-also"></a>См. также  
 [Объект Date](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Date)   
 [Метод GETDATE (Date)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Date/getdate)   
 [Встроенные объекты](https://developer.mozilla.org/docs/Learn/JavaScript/Objects)