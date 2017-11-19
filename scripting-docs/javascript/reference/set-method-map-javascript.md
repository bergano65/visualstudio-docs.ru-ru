---
title: "Метод set (Map) (JavaScript) | Документы Microsoft"
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
ms.assetid: 31ee71a0-b09d-442a-9e02-825accf94ffa
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a84a5b2714fde55fba03d581faa851d7245e001
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="set-method-map-javascript"></a>Метод set (Map) (JavaScript)
Добавляет новый элемент в сопоставление.  
  
## <a name="syntax"></a>Синтаксис  
  
```JavaScript  
mapObj.set(key, value)  
```  
  
#### <a name="parameters"></a>Параметры  
 `mapObj`  
 Обязательный. Объект `Map`.  
  
 `key`  
 Обязательный. Ключ для нового элемента.  
  
 `value`  
 Обязательный. Добавляемое значение элемента.  
  
## <a name="property-valuereturn-value"></a>Значение свойства, возвращаемое значение  
 Возвращает объект `Map`, содержащий новую пару "ключ-значение".  
  
## <a name="remarks"></a>Примечания  
 При добавлении значения в коллекцию с помощью существующего ключа новое значение заменяет старое.  
  
## <a name="example"></a>Пример  
 В следующем примере показано добавление членов в объект `Map` и затем извлечение их.  
  
```JavaScript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
  
m.forEach(function (item) {  
    document.write(item.toString() + "<br />");  
});  
  
// Output:  
// black  
// red  
// 2  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]