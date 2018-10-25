---
title: Ожидается объект даты | Документация Майкрософт
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
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49947645"
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