---
title: "Определение типа (Typedef) JsObjectBeforeCollectCallback | Документы Майкрософт"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f21a064a-579f-44cb-9d21-76b62e8c18f5
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7d11de01c44792d3e41cc2721a404f2ed906f02e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="jsobjectbeforecollectcallback-typedef"></a>JsObjectBeforeCollectCallback Typedef
Обратный вызов, вызываемый перед сбором объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
typedef void (CALLBACK *JsObjectBeforeCollectCallback)(  
  _In_ JsRef ref,  
  _In_opt_ void *callbackState  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ref`  
 Объект для сбора.  
  
 `callbackState`  
 Состояние, переданное в `JsSetObjectBeforeCollectCallback`.  
  
## <a name="remarks"></a>Примечания  
 Этот API поддерживается только в режиме Edge.  
  
## <a name="requirements"></a>Требования  
 jsrt.h  
  
## <a name="see-also"></a>См. также  
 [Справочник (среда выполнения JavaScript)](../chakra-hosting/reference-javascript-runtime.md)