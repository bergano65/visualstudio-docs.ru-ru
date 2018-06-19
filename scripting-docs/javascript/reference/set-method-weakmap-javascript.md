---
title: Метод set (WeakMap) (JavaScript) | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 29fc72b1-224f-4f19-8c06-5d926d695b03
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c916bda13c7bd973b37c4e4cb6b81e327ee5de54
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639604"
---
# <a name="set-method-weakmap-javascript"></a>Метод set (WeakMap) (JavaScript)
Добавляет новый элемент в объект `WeakMap`.  
  
## <a name="syntax"></a>Синтаксис  
  
```JavaScript  
weakmapObj.set(key, value)  
```  
  
#### <a name="parameters"></a>Параметры  
 `weakmapObj`  
 Обязательный. Объект `WeakMap`.  
  
 `key`  
 Обязательный. Объект, представляющий ключ добавляемого элемента. Это должна быть ссылка на объект.  
  
 `value`  
 Обязательный. Добавляемое значение элемента.  
  
## <a name="property-valuereturn-value"></a>Значение свойства, возвращаемое значение  
 Возвращает объект `WeakMap`, содержащий новую пару "ключ-значение".  
  
## <a name="remarks"></a>Примечания  
 При добавлении значения в коллекцию с помощью существующего ключа новое значение заменяет старое.  
  
## <a name="example"></a>Пример  
 В следующем примере показано добавление членов в объект `WeakMap`.  
  
```JavaScript  
var dog = {  
    breed: "yorkie"  
}  
  
var cat = {  
    breed: "burmese"  
}  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
wm.set(cat, "pepper");  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]