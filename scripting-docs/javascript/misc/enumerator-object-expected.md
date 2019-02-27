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
ms.openlocfilehash: 14fcb4d990b03a8e7b896014403eb8dceac66b80
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/26/2019
ms.locfileid: "56841835"
---
# <a name="enumerator-object-expected"></a>Требуется объект Enumerator
Предпринята попытка вызова **Enumerator.prototype.atEnd, Enumerator.prototype.item, Enumerator.prototype.moveFirst,** или **Enumerator.prototype.moveNext** метод на другой тип объекта чем `Enumerator`. Объект этого типа вызова должен иметь тип `Enumerator`. Ниже приведен пример кода, который нарушает это правило:  
  
```JavaScript  
var o = new Object;  
o.f = Enumerator.prototype.atEnd;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Вызывается только **Enumerator.prototype.atEnd**, **Enumerator.prototype.item**, **Enumerator.prototype.moveFirst**, или  **Enumerator.prototype.moveNext** методов в объектах типа `Enumerator`. Чтобы узнать, если объект является `Enumerator` , используйте:  
  
    ```js
    if(x instanceof Enumerator)  
    ```  
  
## <a name="see-also"></a>См. также  
 [Объект Enumerator](../../javascript/reference/enumerator-object-javascript.md)