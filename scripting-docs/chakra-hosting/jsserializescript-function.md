---
title: "Функция JsSerializeScript | Документы Майкрософт"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsSerializeScript
helpviewer_keywords: JsSerializeScript function
ms.assetid: ca42c194-e1c1-407d-b542-b9d494e3ac4e
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 92bc6c1de0f2cd43dfe9566413fb64188fd5a382
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="jsserializescript-function"></a>Функция JsSerializeScript
Сериализует проанализированный скрипт в буфер, который можно использовать повторно.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
STDAPI_(JsErrorCode) JsSerializeScript(  
   _In_z_ const wchar_t *script,  
   _Out_writes_to_opt_(*bufferSize,  
   *bufferSize) BYTE *buffer,  
   _Inout_ unsigned long *bufferSize  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `script`  
 Скрипт для сериализации.  
  
 `buffer`  
 Буфер для размещения сериализованного скрипта. Может быть равен null.  
  
 `bufferSize`  
 Размер буфера в байтах на входе; размер буфера в байтах, необходимый для хранения сериализованного скрипта, на выходе.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Код `JsNoError` , если операция завершилась успешно, если нет, то код сбоя.  
  
## <a name="remarks"></a>Примечания  
 `JsSerializeScript` анализирует скрипт и затем сохраняет проанализированную форму скрипта в независимом от среды выполнения формате. Затем сериализованный скрипт можно десериализовать в любой среде выполнения без повторного анализа.  
  
 Требуется контекст активного скрипта.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jsrt.h  
  
## <a name="see-also"></a>См. также  
 [Справочник (среда выполнения JavaScript)](../chakra-hosting/reference-javascript-runtime.md)