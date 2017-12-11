---
title: "Определение типа (Typedef) JsMemoryAllocationCallback | Документы Майкрософт"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 511babc7-3caa-4ee5-82a2-943bbd34db8d
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9672c23f48a2cb3e20de58012b267b30f4514d66
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="jsmemoryallocationcallback-typedef"></a>Определение типа (Typedef) JsMemoryAllocationCallback
Процедура обратного вызова, реализованная пользователем для событий выделения памяти.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
typedef bool (CALLBACK * JsMemoryAllocationCallback)(  
   _In_opt_ void *callbackState,  
   _In_ JsMemoryEventType allocationEvent,  
   _In_ size_t allocationSize  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 callbackState  
 Состояние, переданное в JsSetRuntimeMemoryAllocationCallback.  
  
 allocationEvent  
 Тип события выделения типа.  
  
 allocationSize  
 Размер выделения.  
  
## <a name="property-valuereturn-value"></a>Значение свойства, возвращаемое значение  
 Для события JsMemoryAllocate event возврат значения "true" позволяет среде выполнения продолжать выделение. Возврат значения "false" показывает, что запрос выделения отклонен. Возвращаемое значение игнорируется другими событиями выделения.  
  
## <a name="remarks"></a>Примечания  
 Используйте JsSetRuntimeMemoryAllocationCallback для регистрации этого обратного вызова.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jsrt.h  
  
## <a name="see-also"></a>См. также  
 [Справочник (среда выполнения JavaScript)](../chakra-hosting/reference-javascript-runtime.md)