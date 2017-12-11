---
title: "Функция JsParseSerializedScriptWithCallback | Документы Майкрософт"
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a93ecfb-4b82-4a85-b24c-6816db2332ea
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 15f531783c7a1018340be8033261a58418d0f515
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="jsparseserializedscriptwithcallback-function"></a>Функция JsParseSerializedScriptWithCallback
Анализирует сериализованный скрипт и возвращает функцию, представляющую этот скрипт.     Предоставляет возможность отложенной загрузки источника скрипта, только если он нужен.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
STDAPI_(JsErrorCode) JsParseSerializedScriptWithCallback(  
  _In_ JsSerializedScriptLoadSourceCallback scriptLoadCallback,  
  _In_ JsSerializedScriptUnloadCallback scriptUnloadCallback,  
  _In_ BYTE *buffer,  
  _In_ JsSourceContext sourceContext,  
  _In_z_ const wchar_t *sourceUrl,  
  _Out_ JsValueRef * result  
);  
  
```  
  
#### <a name="parameters"></a>Параметры  
 `scriptLoadCallback`  
 Обратный вызов выполняется, когда нужно загрузить исходный код скрипта.  
  
 `scriptUnloadCallback`  
 Обратный вызов выполняется, когда сериализованный скрипт и исходный код больше не нужны.  
  
 `buffer`  
 Сериализованный скрипт.  
  
 `sourceContext`  
 Файл cookie, указывающий на скрипт, который может использоваться контекстами отлаживаемых скриптов.     Этот контекст будет передан в scriptLoadCallback и scriptUnloadCallback.  
  
 `sourceUrl`  
 Исходное местоположение скрипта.  
  
 `result`  
 Функция, представляющая код скрипта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Код `JsNoError` , если операция завершилась успешно, если нет, то код сбоя.  
  
## <a name="remarks"></a>Примечания  
  
> [!NOTE]
>  Этот API пока не доступен для приложений Магазина.  
  
 Требуется контекст активного скрипта.  
  
 Среда выполнения будет удерживать буфер, пока все экземпляры любых функций, созданных из буфера, не будут удалены сборкой мусора.  Затем она вызывает scriptUnloadCallback, чтобы уведомить вызывающий объект о том, что освобождение безопасно.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jsrt.h  
  
## <a name="see-also"></a>См. также  
 [Справочник (среда выполнения JavaScript)](../chakra-hosting/reference-javascript-runtime.md)