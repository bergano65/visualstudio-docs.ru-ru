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
ms.openlocfilehash: 969f2bcb578d74ac02a7bdaa6984de5948e49e27
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85817610"
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
 [Объект Date](../../javascript/reference/date-object-javascript.md)   
 [Метод GETDATE (Date)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Встроенные объекты](../../javascript/intrinsic-objects-javascript.md)