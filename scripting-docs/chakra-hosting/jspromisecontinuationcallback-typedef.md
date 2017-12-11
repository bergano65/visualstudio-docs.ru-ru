---
title: "Определение типа (Typedef) JsPromiseContinuationCallback | Документы Майкрософт"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 51a3fd02-9668-4cf7-bb0b-e1fd03b2528f
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 762391cb66e5298bd70beb3238720d3717554ae0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="jspromisecontinuationcallback-typedef"></a>JsPromiseContinuationCallback Typedef
Обратный вызов перспективного продолжения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
typedef void (CALLBACK *JsPromiseContinuationCallback)(  
  _In_ JsValueRef task,  
  _In_opt_ void *callbackState  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `task`  
  `callbackState`  
  
## <a name="remarks"></a>Примечания  
 Узел может указать обратный вызов перспективного продолжения в `JsSetPromiseContinuationCallback`. Если скрипт создает задачу, которая должна быть выполнена позже, то будет вызван обратный вызов перспективного продолжения с задачей, а задача должна быть помещена в очередь FIFO и выполнена после завершения текущего скрипта.  
  
 Этот API поддерживается только в режиме Edge.  
  
## <a name="requirements"></a>Требования  
 jsrt.h  
  
## <a name="see-also"></a>См. также  
 [Справочник (среда выполнения JavaScript)](../chakra-hosting/reference-javascript-runtime.md)