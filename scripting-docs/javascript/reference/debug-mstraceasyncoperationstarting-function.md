---
title: "Функция Debug.msTraceAsyncOperationStarting | Документы Microsoft"
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
ms.assetid: c8458264-07e0-4cd6-8528-ff7cf009cf9e
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a50c58e352d40a06192664cdf7424348be02d466
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="debugmstraceasyncoperationstarting-function"></a>Функция Debug.msTraceAsyncOperationStarting
Инициирует трассировку асинхронной операции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Debug.msTraceAsyncOperationStarting(operationName)  
```  
  
#### <a name="parameters"></a>Параметры  
 `operationName`  
 Обязательный. Строка, определяющая асинхронную операцию. Если параметр `operationName` имеет значение NULL или не определен, в качестве имени операции используется пустая строка.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Целое число, представляющее идентификатор операции.  
  
## <a name="remarks"></a>Примечания  
 Этот метод следует вызывать до начала выполнения асинхронной операции.  
  
> [!NOTE]
>  Некоторые средства отладки не отображают сведения, отправленные в отладчик.  
  
## <a name="example"></a>Пример  
 В следующем коде приведен пример инструментирования асинхронного вызова для приложения [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  
  
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