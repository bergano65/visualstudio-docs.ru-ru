---
title: "Функция JsSetObjectBeforeCollectCallback | Документы Майкрософт"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: ea2cbd94-d8b0-4fa9-a4a1-c75a4e338eaf
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6a472e63afd909ee7bcb74cb2fdd1ae98d6a2938
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="jssetobjectbeforecollectcallback-function"></a>Функция JsSetObjectBeforeCollectCallback
Задает функцию обратного вызова, которая вызывается средой выполнения до сборки мусора для объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
STDAPI_(JsErrorCode) JsSetObjectBeforeCollectCallback(  
   _In_ JsRef ref,  
   _In_opt_ void *callbackState,  
   _In_ JsObjectBeforeCollectCallback objectBeforeCollectCallback  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ref`  
 Объект, для которого необходимо зарегистрировать обратный вызов.  
  
 `callbackState`  
 Предоставляемое пользователем состояние, которое будет передано обратно методу обратного вызова.  
  
 `objectBeforeCollectCallback`  
 Задаваемая функция обратного вызова. Используйте значение NULL для очистки ранее зарегистрированного обратного вызова.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Код `JsNoError` , если операция завершилась успешно, если нет, то код сбоя.  
  
## <a name="remarks"></a>Примечания  
 Обратный вызов выполняется в текущем потоке выполнения среды выполнения, поэтому выполнение блокируется до завершения обратного вызова.  
  
 Этот API поддерживается только в режиме Edge.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jsrt.h  
  
## <a name="see-also"></a>См. также  
 [Справочник (среда выполнения JavaScript)](../chakra-hosting/reference-javascript-runtime.md)