---
title: Ожидается объект перечислителя | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5015
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: dc6e32c1-a6e6-4e12-ac99-e3f65f91c8d7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 06005f635e5173e903cfba6a952750d64181d0bf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62946346"
---
# <a name="enumerator-object-expected"></a>Требуется объект Enumerator
Предпринята попытка вызова **Enumerator.prototype.atEnd, Enumerator.prototype.item, Enumerator.prototype.moveFirst,** или **Enumerator.prototype.moveNext** метод на другой тип объекта чем `Enumerator`. Объект этого типа вызова должен иметь тип `Enumerator`. Ниже приведен пример кода, который нарушает это правило:  
  
```JavaScript  
var o = new Object;  
o.f = Enumerator.prototype.atEnd;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Вызывается только **Enumerator.prototype.atEnd**, **Enumerator.prototype.item**, **Enumerator.prototype.moveFirst**, или  **Enumerator.prototype.moveNext** методов в объектах типа `Enumerator`. Чтобы узнать, если объект является `Enumerator` , используйте:  
  
    ```js
    if(x instanceof Enumerator)  
    ```  
  
## <a name="see-also"></a>См. также  
 [Объект Enumerator](../../javascript/reference/enumerator-object-javascript.md)