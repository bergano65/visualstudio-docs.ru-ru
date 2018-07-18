---
title: Функция JsRunSerializedScriptWithCallback | Документы Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0608d778-f65b-4dc5-a745-364aac57ef59
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ce51c9473100e71831dd53cc6572d9740790ffa0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568864"
---
# <a name="jsrunserializedscriptwithcallback-function"></a>Функция JsRunSerializedScriptWithCallback
Запускает сериализованный скрипт.     Предоставляет возможность отложенной загрузки источника скрипта, только если он нужен.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
STDAPI_(JsErrorCode) JsRunSerializedScriptWithCallback(  
  _In_ JsSerializedScriptLoadSourceCallback scriptLoadCallback,  
  _In_ JsSerializedScriptUnloadCallback scriptUnloadCallback,  
  _In_ BYTE *buffer,  
  _In_ JsSourceContext sourceContext,  
  _In_z_ const wchar_t *sourceUrl,  
  _Out_opt_ JsValueRef *result  
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
 Результат выполнения скрипта (если есть). Этот параметр может быть нулевым.  
  
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