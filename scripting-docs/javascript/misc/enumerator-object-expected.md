---
title: Ожидался объект перечислителя | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: ff61894ce808cd33876e876c596e791a3347ab72
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85817597"
---
# <a name="enumerator-object-expected"></a>Требуется объект Enumerator
Предпринята попытка вызова метода **Enumerator. prototype. atEnd, перечислителя. prototype. Item, перечислителя. prototype. MoveFirst** или **Enumerator. prototype. MoveNext** для объекта типа, отличного от `Enumerator` . Объект этого типа вызова должен иметь тип `Enumerator` . Ниже приведен пример кода, который нарушает это правило:  
  
```JavaScript  
var o = new Object;  
o.f = Enumerator.prototype.atEnd;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Вызываются только методы **Enumerator. prototype. atEnd**, **перечислитель. prototype. Item**, **Enumerator. prototype. MoveFirst**или **Enumerator. prototype. MoveNext** для объектов типа `Enumerator` . Чтобы определить, является ли объект `Enumerator` объектом, используйте:  
  
    ```js
    if(x instanceof Enumerator)  
    ```  
  
## <a name="see-also"></a>См. также  
 [Объект Enumerator](../../javascript/reference/enumerator-object-javascript.md)