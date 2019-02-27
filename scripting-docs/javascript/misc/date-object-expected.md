---
title: Ожидается объект даты | Документация Майкрософт
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
ms.openlocfilehash: a53ff758622cf719c2b10ea47fc516ac8684eb6a
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/26/2019
ms.locfileid: "56842251"
---
# <a name="date-object-expected"></a>Ожидается объект даты
Предпринята попытка вызова **Date.prototype.toString** или **Date.prototype.valueOf** метод на объект типа, отличных от `Date`. Объект этого типа вызова должен иметь тип `Date`. Пример:  
  
```JavaScript  
var o = new Object;  
o.f = Date.prototype.toString;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Вызывается только **Date.prototype.toString** или **Date.prototype.valueOf** методов в объектах типа `Date`.  
  
## <a name="see-also"></a>См. также  
 [Объект Date](../../javascript/reference/date-object-javascript.md)   
 [Метод getDate (Date)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Встроенные объекты](../../javascript/intrinsic-objects-javascript.md)