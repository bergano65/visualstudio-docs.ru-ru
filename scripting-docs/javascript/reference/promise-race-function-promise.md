---
title: Функция Promise.Race (Promise) | Документы Microsoft
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
ms.assetid: 9236eced-d313-4d03-8c3e-d89d762b3084
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d35c448ad143facdcd783df0551505e440521b98
ms.sourcegitcommit: 11740fed01cc602252ef698aaa11c07987b00570
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/12/2018
ms.locfileid: "27782676"
---
# <a name="promiserace-function-promise"></a>Функция Promise.race (Promise)
Создает новый объект Promise, который будет разрешен или отклонен с тем же значением результата, что и первый разрешенный или отклоненный объект Promise в числе переданных аргументов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Promise.race(iterable)  
```  
  
#### <a name="parameters"></a>Параметры  
 `iterable`  
 Обязательно. Один или несколько объектов Promise.  
  
## <a name="remarks"></a>Примечания  
 Если один из объектов Promise в объекте `iterable` уже разрешен или отклонен, `Promise.race` возвращает разрешенный или отклоненный объект Promise в том же виде, а результирующее значение равно значению, которое использовалось для разрешения (или отклонения) этого объекта. Если в объекте `iterable` разрешены или отклонены уже несколько объектов Promise, `Promise.race` возвращает объект Promise, разрешенный таким же образом, как и первый итерированный объект Promise. Если итерируемый объект не содержит разрешенных или отклоненных объектов Promise, объект Promise, возвращенный из `Promise.race`, также не разрешается и не отклоняется.  
  
## <a name="example"></a>Пример  
  
```JavaScript  
var p1 = new Promise(function(resolve, reject) {  
    setTimeout(resolve, 0, 'success');  
});  
var p2 = new Promise(function(resolve, reject) { });  
var p3 = new Promise(function(resolve, reject) { });  
  
var race = Promise.race( [p1, p2, p3] );  
race.then(function(result) {  
    console.log(result);  
});  
  
// Output:  
// success  
  
var race = Promise.race( [Promise.reject('failure'),  
    Promise.resolve('success')] );  
race.catch(function(result) {  
    console.log(result);  
});  
  
// Output:  
// failure  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Объект Promise](../../javascript/reference/promise-object-javascript.md)
