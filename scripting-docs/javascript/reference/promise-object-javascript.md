---
title: Promise объект (JavaScript) | Документы Microsoft
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
ms.assetid: 358ad98b-f7fa-448c-9ee0-ef1e2a45e9c6
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 61e5611dd0d455c7e7b704777cc2341ca43a2404
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640634"
---
# <a name="promise-object-javascript"></a>Объект Promise (JavaScript)
Предоставляет механизм для планирования работы на основе значения, которое еще не было вычислено. Это — абстракция для управления взаимодействиями с асинхронными интерфейсами API.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
var promise = new Promise(function(resolve, reject) { ... });  
```  
  
#### <a name="parameters"></a>Параметры  
 `promise`  
 Обязательный. Имя переменной, которой присваивается объект Promise.  
  
 `resolve`  
 Обязательный. Функция, выполнение которой указывает на то, что объект Promise успешно завершен.  
  
 `reject`  
 Необязательно. Функция, выполнение которой указывает на то, что объект Promise отклонен с ошибкой.  
  
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
  
## <a name="example"></a>Пример  
 Кроме того, вызовы метода `then` можно соединить в цепочку, как показано в следующем коде. При этом каждый обработчик завершения должен выдать свой собственный объект Promise. В данном коде, который вызывает одну и ту же функцию `timeout`, первый вызов возвращает значение через 1 000 мс. Первый обработчик завершения снова вызывает функцию `timeout`, после чего объект Promise возвращается через 2 000 мс. Затем очередной обработчик завершения вызывает ошибку. Обработчик ошибок вызывает функцию `Promise.all`, которая возвращает значение только после того, как оба вызова функции timeout будут завершены или отклонены.  
  
```JavaScript  
var p = timeout(1000).then(() => {  
    return timeout(2000);  
}).then(() => {  
    throw new Error("error");  
}).catch(err => {  
    return Promise.all([timeout(100), timeout(200)]);  
})  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="functions"></a>Функции  
 В следующей таблице описаны функции объекта `Promise`.  
  
|Функция|Описание|  
|--------------|-----------------|  
|[Функция Promise.all](../../javascript/reference/promise-all-function-promise.md)|Соединяет два или более объекта Promise и возвращает значение только после завершения или отклонения всех этих объектов.|  
|[Функция Promise.Race](../../javascript/reference/promise-race-function-promise.md)|Создает новый объект Promise, который будет разрешен или отклонен с тем же значением результата, что и первый разрешенный или отклоненный объект Promise в числе переданных аргументов.|  
|[Функция Promise.Reject](../../javascript/reference/promise-reject-function-promise.md)|Создает новый отклоненный объект Promise с результатом, равным переданному аргументу.|  
|[Функция Promise.Resolve](../../javascript/reference/promise-resolve-function-promise.md)|Создает новый разрешенный объект Promise с результатом, равным его аргументу.|  
  
## <a name="methods"></a>Методы  
 В следующей таблице описаны методы объекта `Promise`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[Метод catch](../../javascript/reference/catch-method-promise.md)|Позволяет указать, какое действие следует выполнить при отклонении объекта Promise.|  
|[Затем метод](../../javascript/reference/then-method-promise.md)|Позволяет указать, какое действие следует выполнить при выполнении объекта Promise.|