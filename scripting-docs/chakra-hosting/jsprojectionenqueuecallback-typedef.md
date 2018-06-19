---
title: Определение типа (Typedef) JsProjectionEnqueueCallback | Документы Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 19c1cefb-a7be-4196-b780-9fe6adf35ba5
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bda4a3a80edac38ab2c3885c2256cdf9d03eb8c1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568314"
---
# <a name="jsprojectionenqueuecallback-typedef"></a>JsProjectionEnqueueCallback Typedef
Обратный вызов приложения, который вызывается средой JsRT, когда API проекции выполняется не в исходном, а в другом потоке.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
typedef void (CALLBACK *JsProjectionEnqueueCallback)(  
  _In_ JsProjectionCallback jsCallback,  
  _In_ JsProjectionCallbackContext jsContext,  
  _In_opt_ void *callbackState  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `jsCallback`  
 Обратный вызов, который должен вызываться в исходном потоке.  
  
 `jsContext`  
 Контекст приложений.  
  
 `callbackState`  
 Контекст JsRT, который должен быть передан в `jsCallback`.  
  
## <a name="remarks"></a>Примечания  
 Требует вызова JsSetProjectionEnqueueCallback для получения обратных вызовов.  
  
 Этот API поддерживается только в режиме Edge.  
  
## <a name="requirements"></a>Требования  
 jsrt.h  
  
## <a name="see-also"></a>См. также  
 [Справочник (среда выполнения JavaScript)](../chakra-hosting/reference-javascript-runtime.md)