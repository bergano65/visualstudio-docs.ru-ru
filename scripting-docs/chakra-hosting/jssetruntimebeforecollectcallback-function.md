---
title: "Функция JsSetRuntimeBeforeCollectCallback | Документы Майкрософт"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsSetRuntimeBeforeCollectCallback
helpviewer_keywords: JsSetRuntimeBeforeCollectCallback function
ms.assetid: 7b2fb911-6007-4ed9-a307-66cefe590ea4
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 469b33a324f67d17bd6f5156da7cce169b98c663
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="jssetruntimebeforecollectcallback-function"></a>Функция JsSetRuntimeBeforeCollectCallback
Задает функцию обратного вызова, которая вызывается средой выполнения до сборки мусора.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
STDAPI_(JsErrorCode) JsSetRuntimeBeforeCollectCallback(  
   _In_ JsRuntimeHandle runtime,  
   _In_opt_ void *callbackState,  
   _In_ JsBeforeCollectCallback beforeCollectCallback  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `runtime`  
 Среда выполнения, для которой необходимо зарегистрировать обратный вызов выделения.  
  
 `callbackState`  
 Предоставляемое пользователем состояние, которое будет передано обратно методу обратного вызова.  
  
 `beforeCollectCallback`  
 Задаваемая функция обратного вызова.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Код `JsNoError` , если операция завершилась успешно, если нет, то код сбоя.  
  
## <a name="remarks"></a>Примечания  
 Обратный вызов выполняется в текущем потоке выполнения среды выполнения, поэтому выполнение блокируется до завершения обратного вызова.  
  
 Обратный вызов может использоваться хостами для подготовки к сборке мусора. Например, путем удаления ненужных ссылок в объектах Chakra.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jsrt.h  
  
## <a name="see-also"></a>См. также  
 [Справочник (среда выполнения JavaScript)](../chakra-hosting/reference-javascript-runtime.md)