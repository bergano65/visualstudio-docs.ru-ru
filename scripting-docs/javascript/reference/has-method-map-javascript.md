---
title: "Метод has (Map) (JavaScript) | Документы Microsoft"
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
ms.assetid: 876df854-2941-4db2-92c6-1b497840b169
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 48228b495c845bef91caa0b85e67980100a6f790
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="has-method-map-javascript"></a>Метод has (Map) (JavaScript)
Возвращает `true` Если сопоставление содержит указанный элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```JavaScript  
mapObj.has(key)  
```  
  
#### <a name="parameters"></a>Параметры  
 `mapObj`  
 Обязательный. Объект `Map`.  
  
 `key`  
 Обязательный. Ключ элемента, который требуется проверить.  
  
## <a name="property-valuereturn-value"></a>Значение свойства, возвращаемое значение  
 `true`Если сопоставление содержит указанный элемент.  
  
## <a name="example"></a>Пример  
 Следующий пример демонстрирует добавление члена `Map` и проверьте, содержит ли объект map его.  
  
```JavaScript  
var m = new Map();  
m.set(2, "red");  
  
document.write(m.has(2));  
  
// Output:  
// true  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]