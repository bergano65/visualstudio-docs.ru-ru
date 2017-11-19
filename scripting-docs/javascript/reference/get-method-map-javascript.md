---
title: "Метод GET (Map) (JavaScript) | Документы Microsoft"
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
ms.assetid: bebbd6bc-6e61-4674-8196-7e907798973f
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 243d5aa93289cb7a13b34567b7824d028151bad3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="get-method-map-javascript"></a>Метод get (Map) (JavaScript)
Возвращает указанный элемент из сопоставления.  
  
## <a name="syntax"></a>Синтаксис  
  
```JavaScript  
mapObj.get(key)  
```  
  
#### <a name="parameters"></a>Параметры  
 `mapObj`  
 Обязательный. Объект `Map`.  
  
 `key`  
 Обязательный. Ключ элемента в `Map`.  
  
## <a name="property-valuereturn-value"></a>Значение свойства, возвращаемое значение  
 Возвращает объект, связанный с ключом. Если `Map` не содержит ключ, этот метод возвращает `undefined` значение.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как получить элемент из `Map` объекта.  
  
```JavaScript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
  
document.write(m.get(2));  
  
// Output:  
// red  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]