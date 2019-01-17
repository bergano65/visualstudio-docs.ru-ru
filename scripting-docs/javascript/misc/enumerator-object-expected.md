---
title: Ожидается объект перечислителя | Документация Майкрософт
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
ms.openlocfilehash: 002c3a748af8f7fa5c21109adcb279f893b38965
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2019
ms.locfileid: "54347246"
---
# <a name="enumerator-object-expected"></a>Ожидается объект перечислителя
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