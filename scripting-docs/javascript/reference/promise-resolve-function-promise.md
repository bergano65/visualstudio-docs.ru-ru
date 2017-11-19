---
title: "Функция Promise.Resolve (Promise) | Документы Microsoft"
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
ms.assetid: 0fb6bff9-54ab-41be-97d7-04f7e6fe9cff
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6d815c9c23da48c877f7f1d995df8991429375e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="promiseresolve-function-promise"></a>Функция Promise.resolve (Promise)
Создает новый разрешенный объект Promise с результатом, равным его аргументу.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Promise.resolve(x)  
```  
  
#### <a name="parameters"></a>Параметры  
 `x`  
 Обязательный. Значение, возвращаемое с завершенным объектом Promise.  
  
## <a name="remarks"></a>Примечания  
 Функция обработки исполнения метода `then` выполняется при возвращении завершенного объекта Promise.  
  
## <a name="example"></a>Пример  
  
```JavaScript  
var p = Promise.resolve('success');  
p.then(function(result) {  
    console.log(result);  
});  
  
// Output:  
// success  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Объект Promise](../../javascript/reference/promise-object-javascript.md)