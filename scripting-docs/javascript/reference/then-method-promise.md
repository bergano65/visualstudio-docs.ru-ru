---
title: "Метод Then (Promise) | Документы Microsoft"
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
ms.assetid: c7f3259d-78f7-4ca7-8bdf-99fbd3f41e8d
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eeb97fae19ca9923280b5099e3e4d8c839fa2815
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="then-method-promise"></a>Метод then (Promise)
Позволяет указать, какое действие следует выполнить при выполнении объекта Promise.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
promise.then(onCompleted, onRejected);  
```  
  
#### <a name="parameters"></a>Параметры  
 `promise`  
 Обязательный. Объект Promise.  
  
 `onCompleted`  
 Обязательный. Функция обработчика исполнения, которая будет выполняться при успешном завершении объекта Promise.  
  
 `onRejected`  
 Необязательно. Функция обработчика ошибок, которая будет выполняться при отклонении объекта Promise.  
  
## <a name="remarks"></a>Примечания  
 Объект Promise должен быть либо завершен с определенным значением, либо отклонен по какой-либо причине. Метод `then` объекта Promise выполняется при завершении или отклонении объекта Promise в зависимости от того, что произойдет раньше. Если объект Promise завершается, запускается функция обработчика исполнения метода `then`. Если объект Promise отклоняется, запускается обработчик ошибок метода `then` (или метода `catch`).  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как вызвать функцию (`timeout`), которая возвращает объект Promise. Обработчик завершения метода `then` запускается по истечении периода ожидания, составляющего 5 000 мс.  
  
```JavaScript  
function timeout(duration) {  
    return new Promise(function(resolve, reject) {  
        setTimeout(resolve, duration);  
    });  
}  
  
// Note: This code uses arrow function syntax  
var m = timeout(5000).then(() => {  
    console.log("done!");  
})  
  
// Output (after 5 seconds):  
// done!  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Объект Promise](../../javascript/reference/promise-object-javascript.md)