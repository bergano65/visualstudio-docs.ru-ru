---
title: "Функция JsSetProjectionEnqueueCallback | Документы Майкрософт"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: c751ccef-20d2-4d41-9568-1c54adf47cdf
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8abdc575c5066ade4a700a0c88e09e3476a65366
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="jssetprojectionenqueuecallback-function"></a>Функция JsSetProjectionEnqueueCallback
Устанавливает обратный вызов, который должен использоваться для вызова завершения проекции обратно в необходимом потоке вызывающих объектов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
STDAPI_(JsErrorCode) JsSetProjectionEnqueueCallback(  
   _In_ JsProjectionEnqueueCallback projectionEnqueueCallback,  
   _In_opt_ void *projectionEnqueueContext);  
  
```  
  
#### <a name="parameters"></a>Параметры  
 `projectionEnqueueContext`  
 Обратный вызов, который будет вызываться каждый раз, когда в фоновом потоке происходит завершение проекции.  
  
 `callbackState`  
 Контекст приложения, предоставляемый в `projectionEnqueueContext`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Код `JsNoError` , если операция завершилась успешно, если нет, то код сбоя.  
  
## <a name="remarks"></a>Примечания  
 Требуется контекст активного скрипта.  
  
 Вызов должен поступать из другого контейнера COM или из другого потока в том же MTA.  
  
 Этот API поддерживается только в режиме Edge.  
  
> [!CAUTION]
>  В настоящее время PInvoke не поддерживается для этого интерфейса API.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jsrt.h  
  
## <a name="see-also"></a>См. также  
 [Справочник (среда выполнения JavaScript)](../chakra-hosting/reference-javascript-runtime.md)