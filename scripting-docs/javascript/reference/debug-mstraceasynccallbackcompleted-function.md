---
title: Функция Debug.msTraceAsyncCallbackCompleted | Документы Microsoft
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
ms.assetid: 6f9bf139-a6f0-4d91-b7bf-bcc0515de686
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 952aa3cd1b5c1c223a438c825ac1d97466db86ff
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636084"
---
# <a name="debugmstraceasynccallbackcompleted-function"></a>Функция Debug.msTraceAsyncCallbackCompleted
Указывает, что стек обратных вызовов, связанный с ранее определенной асинхронной операцией, завершился.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Debug.msTraceAsyncCallbackCompleted()  
```  
  
## <a name="remarks"></a>Примечания  
 Вызывайте эту функцию после вызова `Debug.msTraceAsyncCallbackStarting`.  
  
> [!NOTE]
>  Некоторые средства отладки не отображают сведения, отправленные в отладчик.  
  
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