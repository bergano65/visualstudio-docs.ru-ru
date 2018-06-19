---
title: Метод GET (WeakMap) (JavaScript) | Документы Microsoft
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
ms.assetid: d922c55d-486d-4feb-aedc-1f4867c417d2
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 29decb7e6a050188b75639eb7cf4f27494b31da2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636494"
---
# <a name="get-method-weakmap-javascript"></a>Метод get (WeakMap) (JavaScript)
Возвращает указанный элемент из `WeakMap` объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```JavaScript  
weakmapObj.get(key)  
```  
  
#### <a name="parameters"></a>Параметры  
 `weakmapObj`  
 Обязательный. Объект `WeakMap`.  
  
 `key`  
 Обязательный. Ключ элемента в `WeakMap`.  
  
## <a name="property-valuereturn-value"></a>Значение свойства, возвращаемое значение  
 Возвращает объект, связанный с ключом. Если `WeakMap` не содержит ключ, этот метод возвращает `undefined` значение.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как для получения элементов из `WeakMap` объекта.  
  
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
  
document.write(wm.get(dog) + ": ");  
document.write(dog.breed);  
document.write("<br />");  
document.write(wm.get(cat) + ": ");  
document.write(cat.breed);  
  
// Output:  
// fido: yorkie  
// pepper: burmese  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]