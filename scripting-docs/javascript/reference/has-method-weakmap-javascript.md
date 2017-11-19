---
title: "Метод has (WeakMap) (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 12bedca1-bde7-413a-a4e2-06c03559044f
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e9a1706a1b96b5273ec280c4cef2be47a3bc6e17
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="has-method-weakmap-javascript"></a>Метод has (WeakMap) (JavaScript)
Возвращает `true` Если `WeakMap` содержит указанный элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```JavaScript  
weakmapObj.has(key)  
```  
  
#### <a name="parameters"></a>Параметры  
 `weakmapObj`  
 Обязательный. Объект `WeakMap`.  
  
 `key`  
 Обязательный. Ключ элемента, который требуется проверить.  
  
## <a name="property-valuereturn-value"></a>Значение свойства, возвращаемое значение  
 `true`Если `WeakMap` содержит указанный ключ.  
  
## <a name="example"></a>Пример  
 Следующий пример демонстрирует добавление члена `WeakMap` , а затем используйте `has` Чтобы проверить, присутствует ли он.  
  
```JavaScript  
var dog = {  
    breed: "yorkie"  
}  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
  
document.write(wm.has(dog));  
  
// Output:  
// true  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]