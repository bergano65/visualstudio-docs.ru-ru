---
title: "Определение типа (Typedef) JsProjectionCallbackContext | Документы Майкрософт"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 50c705c5-664f-4a1a-92f6-4882fc718ab1
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7548dc14ab4b3dddc1633a1ba948aba564d8438a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="jsprojectioncallbackcontext-typedef"></a>JsProjectionCallbackContext Typedef
Контекст, передаваемый в обратный вызов приложения (JsProjectionEnqueueCallback) из JsRT, а затем передаваемый приложением обратно в JsRT в предоставленном обратном вызове (`JsProjectionCallback`) в правильном потоке.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
typedef void *JsProjectionCallbackContext;  
```  
  
## <a name="remarks"></a>Примечания  
 Требует вызова `JsSetProjectionEnqueueCallback` для получения обратных вызовов.  
  
 Этот API поддерживается только в режиме Edge.  
  
## <a name="requirements"></a>Требования  
 jsrt.h  
  
## <a name="see-also"></a>См. также  
 [Справочник (среда выполнения JavaScript)](../chakra-hosting/reference-javascript-runtime.md)