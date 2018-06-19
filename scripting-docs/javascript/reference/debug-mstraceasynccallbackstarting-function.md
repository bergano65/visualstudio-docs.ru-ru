---
title: Функция Debug.msTraceAsyncCallbackStarting | Документы Microsoft
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
ms.assetid: 0e2ca7c4-103c-44f2-b76c-102fb1e42543
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 49203cdf16e7cbd74493c882d9cf17b7629da79a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636254"
---
# <a name="debugmstraceasynccallbackstarting-function"></a>Функция Debug.msTraceAsyncCallbackStarting
Связывает стек обратных вызовов с ранее определенной асинхронной операцией.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Debug.msTraceAsyncCallbackStarting(asyncOperationId)  
```  
  
#### <a name="parameters"></a>Параметры  
 `asyncOperationId`  
 Обязательный. Идентификатор, связанный с асинхронной операцией.  
  
## <a name="remarks"></a>Примечания  
 Вызывайте эту функцию в функции обратного вызова для асинхронной операции после вызова `Debug.msTraceAsyncOperationCompleted`.  
  
> [!NOTE]
>  Некоторые средства отладки не отображают сведения, отправленные в отладчик.  
  
 Значение параметра `asyncOperationId` должно соответствовать имени операции, ранее возвращенному из `Debug.msTraceAsyncOperationStarting`.  
  
## <a name="example"></a>Пример  
 Ниже приведен пример кода трассировки асинхронного вызова для приложения [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  
  
```JavaScript  
function asyncWrapperFunction() {  
    var opID = Debug.msTraceAsyncOperationStarting('async trace');  
    doSomethingAsync().then(function (result) {  
        Debug.msTraceAsyncOperationCompleted(opID, Debug.MS_ASYNC_OP_STATUS_SUCCESS);  
        Debug.msTraceAsyncCallbackStarting(opID);  
        // Process result of async operation.  
    }, function (error) {  
        Debug.msTraceAsyncOperationCompleted(opID, Debug.MS_ASYNC_OP_STATUS_ERROR);  
        Debug.msTraceAsyncCallbackStarting(opID);  
    });  
  
    Debug.msTraceAsyncCallbackCompleted();  
}  
  
function doSomethingAsync() {  
    return WinJS.Promise.as(true);  
}  
  
asyncWrapperFunction();  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]