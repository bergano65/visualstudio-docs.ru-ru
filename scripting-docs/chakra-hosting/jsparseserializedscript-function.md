---
title: Функция JsParseSerializedScript | Документы Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- jsrt/JsParseSerializedScript
helpviewer_keywords:
- JsParseSerializedScript function
ms.assetid: 40d0c7c4-fd5b-46ed-9e65-38c2db2fc859
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7eb18c8537d7bdfe69969293b66a5909ba7c3fa1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568684"
---
# <a name="jsparseserializedscript-function"></a>Функция JsParseSerializedScript
Анализирует сериализованный скрипт и возвращает функцию, представляющую этот скрипт.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
STDAPI_(JsErrorCode) JsParseSerializedScript(  
   _In_z_ const wchar_t *script,  
   _In_ BYTE *buffer,  
   _In_ JsSourceContext sourceContext,  
   _In_z_ const wchar_t *sourceUrl,  
   _Out_ JsValueRef *result  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `script`  
 Скрипт для анализа.  
  
 `buffer`  
 Сериализованный скрипт.  
  
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
  
 Буфер не сохраняется в памяти обработчика скриптов, поэтому код должен поддерживать его в активном состоянии столь долго, сколько он может использоваться для выполнения скриптов.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jsrt.h  
  
## <a name="see-also"></a>См. также  
 [Справочник (среда выполнения JavaScript)](../chakra-hosting/reference-javascript-runtime.md)