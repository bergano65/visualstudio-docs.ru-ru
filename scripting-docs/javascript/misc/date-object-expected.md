---
title: Ожидается объект даты | Документы Microsoft
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
- VS.WebClient.Help.SCRIPT5006
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: d6ab82e6-ca64-46b4-a06c-5c6b0aa057cb
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 05e27b822f933ade811084552f6f0379257ae82e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633204"
---
# <a name="date-object-expected"></a>Ожидается объект даты
Предпринята попытка вызвать **Date.prototype.toString** или **Date.prototype.valueOf** метода объекта типа, отличного от `Date`. Объект вызова этого типа должен иметь тип `Date`. Например:  
  
```JavaScript  
var o = new Object;  
o.f = Date.prototype.toString;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Вызывать только **Date.prototype.toString** или **Date.prototype.valueOf** методов для объектов типа `Date`.  
  
## <a name="see-also"></a>См. также  
 [Объект Date](../../javascript/reference/date-object-javascript.md)   
 [Метод getDate (Date)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Встроенные объекты](../../javascript/intrinsic-objects-javascript.md)