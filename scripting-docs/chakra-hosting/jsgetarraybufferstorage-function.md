---
title: Функция JsGetArrayBufferStorage | Документы Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 712ae298-36a9-47ef-b089-e51835c056bc
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a667325eb4d1d9540751a52232e5e06b3004b8b5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568184"
---
# <a name="jsgetarraybufferstorage-function"></a>Функция JsGetArrayBufferStorage
Получает базовое хранилище памяти, которое использует `ArrayBuffer`.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
JsErrorCode STDAPI_ JsGetArrayBufferStorage(  
   _In_ JsValueRef arrayBuffer,  
   _Outptr_result_bytebuffer_(*bufferLength) BYTE **buffer,  
   _Out_ unsigned int *bufferLength  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `arrayBuffer`  
 Экземпляр ArrayBuffer.  
  
 `buffer`  
 Буфер ArrayBuffer. Время жизни возвращаемого буфера совпадает с временем жизни для `ArrayBuffer`. Указатель буфера не учитывается как ссылка на `ArrayBuffer` с целью сборки мусора.  
  
 `bufferLength`  
 Количество байтов в буфере.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Код `JsNoError` , если операция завершилась успешно, если нет, то код сбоя.  
  
## <a name="remarks"></a>Примечания  
 Требуется контекст активного скрипта.  
  
 Этот API поддерживается только в режиме Edge.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jsrt.h  
  
## <a name="see-also"></a>См. также  
 [Справочник (среда выполнения JavaScript)](../chakra-hosting/reference-javascript-runtime.md)