---
title: Функция JsSetRuntimeMemoryAllocationCallback | Документы Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- jsrt/JsSetRuntimeMemoryAllocationCallback
helpviewer_keywords:
- JsSetRuntimeMemoryAllocationCallback function
ms.assetid: 6aa7d58d-6456-4df1-815f-1ba36fb4ae14
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 755ab36c8edb8c0350eb2b245e060344c8825dee
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569074"
---
# <a name="jssetruntimememoryallocationcallback-function"></a>Функция JsSetRuntimeMemoryAllocationCallback
Задает обратный вызов выделения памяти для указанной среды выполнения  
  
## <a name="syntax"></a>Синтаксис  
  
```  
STDAPI_(JsErrorCode) JsSetRuntimeMemoryAllocationCallback(  
   _In_ JsRuntimeHandle runtime,  
   _In_opt_ void *callbackState,  
   _In_ JsMemoryAllocationCallback allocationCallback  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `runtime`  
 Среда выполнения, для которой необходимо зарегистрировать обратный вызов выделения.  
  
 `callbackState`  
 Предоставляемое пользователем состояние, которое будет передано обратно методу обратного вызова.  
  
 `allocationCallback`  
 Обратный вызов выделения памяти, который необходимо выполнять для событий выделения памяти.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Код `JsNoError` , если операция завершилась успешно, если нет, то код сбоя.  
  
## <a name="remarks"></a>Примечания  
 При регистрации обратного вызова выделения памяти среда выполнения выполняет обратный вызов узла всякий раз, когда получает память от операционной системы или освобождает память для ОС. Процедура обратного вызова вызывается, прежде чем диспетчер памяти среды выполнения выделяет блок памяти. Выделение будет отклонено, если обратный вызов возвращает значение false. Диспетчер памяти среды выполнения также вызовет процедуру обратного вызова после освобождения блока памяти, а также после ошибок выделения.  
  
 Обратный вызов выполняется в текущем потоке выполнения среды выполнения, поэтому выполнение блокируется до завершения обратного вызова.  
  
 Возвращаемое значение функции обратного вызова не сохраняется; ранее отклоненные выделения не препятствуют вызову метода обратного вызова средой выполнения в будущем для новых выделений памяти.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jsrt.h  
  
## <a name="see-also"></a>См. также  
 [Справочник (среда выполнения JavaScript)](../chakra-hosting/reference-javascript-runtime.md)