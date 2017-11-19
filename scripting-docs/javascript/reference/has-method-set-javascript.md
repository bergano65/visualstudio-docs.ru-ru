---
title: "Метод has (Set) (JavaScript) | Документы Microsoft"
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
ms.assetid: fb80f2e0-fc5e-4508-af14-1c3b3b833636
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9690e3d091e8ae0f9670fd737a29590524834c9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="has-method-set-javascript"></a>Метод has (Set) (JavaScript)
Возвращает `true` Если набор содержит указанный элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```JavaScript  
setObj.has(value)  
```  
  
#### <a name="parameters"></a>Параметры  
 `setObj`  
 Обязательный. Объект `Set`.  
  
 `value`  
 Обязательный. Элемент для проверки.  
  
## <a name="property-valuereturn-value"></a>Значение свойства, возвращаемое значение  
 `true`, если набор содержит указанный элемент.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как добавлять элементы в `Set`, а затем проверять, содержит ли набор конкретный элемент.  
  
```JavaScript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
  
document.write(s.has(1776));  
document.write(s.has("1776"));  
  
// Output:  
// true  
// false  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]