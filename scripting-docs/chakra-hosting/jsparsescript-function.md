---
title: "Функция JsParseScript | Документы Майкрософт"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsParseScript
helpviewer_keywords:
- JsParseScript function
ms.assetid: e9d0e363-7cbe-43eb-9dc0-1f47e586c9ab
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de55c249b6fb5b723086f48312904f0232f0a11b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="jsparsescript-function"></a>Функция JsParseScript
Анализирует скрипт и возвращает функцию, представляющую скрипт.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
STDAPI_(JsErrorCode) JsParseScript(  
   _In_z_ const wchar_t *script,  
   _In_ JsSourceContext sourceContext,  
   _In_z_ const wchar_t *sourceUrl,  
   _Out_ JsValueRef *result  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `script`  
 Скрипт для анализа.  
  
 `sourceContext`  
 Файл cookie, указывающий на скрипт, который может использоваться контекстами отлаживаемых скриптов.  
  
 `sourceUrl`  
 Исходное местоположение скрипта.  
  
 `result`  
 Функция, представляющая код скрипта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Код `JsNoError` , если операция завершилась успешно, если нет, то код сбоя.  
  
## <a name="remarks"></a>Примечания  
 Требуется контекст активного скрипта.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jsrt.h  
  
## <a name="see-also"></a>См. также  
 [Справочник (среда выполнения JavaScript)](../chakra-hosting/reference-javascript-runtime.md)