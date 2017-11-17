---
title: "Функция Promise.all (Promise) | Документы Microsoft"
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
ms.assetid: 02a7b90c-96f6-4484-9466-d261efa1b494
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 997a419a990b407ae018f7da39fd75673ea28b6d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="promiseall-function-promise"></a>Функция Promise.all (Promise)
Соединяет два или более объекта Promise и возвращает значение только после завершения или отклонения всех этих объектов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Promise.all(func1, func2 [,funcN])  
```  
  
#### <a name="parameters"></a>Параметры  
 `func1`  
 Обязательный. Функция, которая возвращает объект Promise.  
  
 `func2`  
 Обязательный. Функция, которая возвращает объект Promise.  
  
 `funcN`  
 Необязательно. Одна или несколько функций, которые возвращают объект Promise.  
  
## <a name="remarks"></a>Примечания  
 Возвращаемый результат представляет собой массив значений, возвращенных завершенными объектами Promise. Если какой-либо из объединяемых объектов Promise отклоняется, функция `Promise.all` возвращает причину отклонения (все остальные возвращенные значения не учитываются).  
  
## <a name="example"></a>Пример  
 В данном коде первый вызов функции timeout возвращает значение через 5 000 мс. Обработчик завершения вызывает функцию `Promise.all`, которая возвращает значение только после того, как оба вызова функции timeout будут завершены или отклонены.  
  
```JavaScript  
function timeout(duration) {  
    return new Promise(function(resolve, reject) {  
        setTimeout(resolve, duration);  
    });  
}  
  
var p = timeout(5000).then(() => {  
    return Promise.all([timeout(100), timeout(200)]);  
})  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Объект Promise](../../javascript/reference/promise-object-javascript.md)