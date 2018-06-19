---
title: Ожидается объект перечислителя | Документы Microsoft
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
- VS.WebClient.Help.SCRIPT5015
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: dc6e32c1-a6e6-4e12-ac99-e3f65f91c8d7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 485e6e387f07fd3a54727f5f8e08c0a00743c6d9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24632844"
---
# <a name="enumerator-object-expected"></a>Ожидается объект перечислителя
Предпринята попытка вызвать **Enumerator.prototype.atEnd, Enumerator.prototype.item, Enumerator.prototype.moveFirst,** или **Enumerator.prototype.moveNext** метода для объекта типа других чем `Enumerator`. Объект вызова этого типа должен иметь тип `Enumerator`. Ниже приведен пример кода, который нарушает это правило:  
  
```JavaScript  
var o = new Object;  
o.f = Enumerator.prototype.atEnd;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Вызывать только **Enumerator.prototype.atEnd**, **Enumerator.prototype.item**, **Enumerator.prototype.moveFirst**, или  **Enumerator.prototype.moveNext** методов для объектов типа `Enumerator`. Чтобы узнать, если объект является `Enumerator` , используйте:  
  
    ```  
    if(x instanceof Enumerator)  
    ```  
  
## <a name="see-also"></a>См. также  
 [Объект Enumerator](../../javascript/reference/enumerator-object-javascript.md)