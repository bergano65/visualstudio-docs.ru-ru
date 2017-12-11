---
title: "Определение типа (Typedef) JsProjectionCallback | Документы Майкрософт"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 32f22d37-e57e-4196-b6cd-a3fc75bd0632
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 80d1c64f04f44a8560c25935fba2a48905a73260
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="jsprojectioncallback-typedef"></a>JsProjectionCallback Typedef
Обратный вызов JsRT, который должен вызываться с контекстом, передаваемым в `JsProjectionEnqueueCallback` в правильном потоке.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
typedef void (CALLBACK *JsProjectionCallback)(  
  _In_ JsProjectionCallbackContext jsContext  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `jsContext`  
 Требует вызова `JsSetProjectionEnqueueCallback` для получения обратных вызовов.  
  
## <a name="remarks"></a>Примечания  
 Этот API поддерживается только в режиме Edge.  
  
## <a name="requirements"></a>Требования  
 jsrt.h  
  
## <a name="see-also"></a>См. также  
 [Справочник (среда выполнения JavaScript)](../chakra-hosting/reference-javascript-runtime.md)