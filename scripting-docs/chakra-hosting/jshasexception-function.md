---
title: "Функция JsHasException | Документы Майкрософт"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsHasException
helpviewer_keywords:
- JsHasException function
ms.assetid: ac7da3ce-c746-4154-bbb8-bcb0859a8d5b
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 32334f4b8787bebaffb9553fcdd40f85334462cb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="jshasexception-function"></a>Функция JsHasException
Определяет, находится ли среда выполнения текущего контекста в состоянии исключения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
STDAPI_(JsErrorCode) JsHasException(  
   _Out_ bool *hasException  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `hasException`  
 Указывает, находится ли среда выполнения текущего контекста в состоянии исключения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Код `JsNoError` , если операция завершилась успешно, если нет, то код сбоя.  
  
## <a name="remarks"></a>Примечания  
 Если вызов среды выполнения приводит к исключению (в результате выполнения сценария или, например, ошибки преобразования), среда выполнения помещается в состояние исключения. Все вызовы, адресованные любому созданному средой выполнения контексту (кроме API исключения), будут завершаться сбоем с состоянием ошибки `JsErrorInExceptionState` до тех пор, пока исключение не будет очищено.  
  
 Если среда выполнения текущего контекста находится в состоянии исключения, когда обратный вызов возвращается в подсистему, эта подсистема автоматически создаст исключение повторно.  
  
 Требуется контекст активного скрипта.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jsrt.h  
  
## <a name="see-also"></a>См. также  
 [Справочник (среда выполнения JavaScript)](../chakra-hosting/reference-javascript-runtime.md)