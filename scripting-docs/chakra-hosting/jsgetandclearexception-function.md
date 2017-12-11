---
title: "Функция JsGetAndClearException | Документы Майкрософт"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsGetAndClearException
helpviewer_keywords: JsGetAndClearException function
ms.assetid: 6aec8a88-41ee-47f6-b5f4-32f3cae6bb7b
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3e7e4f89bac59aa776762586ab20fa831b5c24bf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="jsgetandclearexception-function"></a>Функция JsGetAndClearException
Возвращает исключение, которое вызвало переход среды выполнения текущего контекста в состояние исключения, и сбрасывает состояние исключения для этой среды выполнения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
STDAPI_(JsErrorCode) JsGetAndClearException(  
   _Out_ JsValueRef *exception  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `exception`  
 Исключение среды выполнения текущего контекста.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Код `JsNoError` , если операция завершилась успешно, если нет, то код сбоя.  
  
## <a name="remarks"></a>Примечания  
 Если среда выполнения текущего контекста не находится в состоянии исключения, этот API возвращает `JsErrorInvalidArgument`. Если среда выполнения отключена, возвращается исключение, указывающее, что сценарий был завершен, однако исключение не удаляется (исключение будет удалено, если среда выполнения включается повторно с использованием метода `JsEnableRuntimeExecution`).  
  
 Требуется контекст активного скрипта.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jsrt.h  
  
## <a name="see-also"></a>См. также  
 [Справочник (среда выполнения JavaScript)](../chakra-hosting/reference-javascript-runtime.md)