---
title: "Функция JsStringToPointer | Документы Майкрософт"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsStringToPointer
helpviewer_keywords: JsStringToPointer function
ms.assetid: c7aa7a09-489d-4435-8f8a-aeb62f8875ae
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ff84f929833941fed9a709497dc615189c39386
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="jsstringtopointer-function"></a>Функция JsStringToPointer
Извлекает указатель на строку, относящийся к строковому значению.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
STDAPI_(JsErrorCode) JsStringToPointer(  
   _In_ JsValueRef value,  
   _Outptr_result_buffer_(*stringLength) const wchar_t **stringValue,  
   _Out_ size_t *stringLength  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `value`  
 Строковое значение, которое необходимо преобразовать в указатель на строку.  
  
 `stringValue`  
 Указатель на строку.  
  
 `stringLength`  
 Длина строки.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Код `JsNoError` , если операция завершилась успешно, если нет, то код сбоя.  
  
## <a name="remarks"></a>Примечания  
 Эта функция извлекает указатель на строку, относящийся к строковому значению. Она завершится сбоем с аргументом `JsErrorInvalidArgument`, если тип значения — не строка. Возвращенное время существования строки совпадать со временем существования значения, из которого оно появилось, однако указатель на строку не считается ссылкой на значение (и поэтому это не воспрепятствует его сбору).  
  
 Требуется контекст активного скрипта.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jsrt.h  
  
## <a name="see-also"></a>См. также  
 [Справочник (среда выполнения JavaScript)](../chakra-hosting/reference-javascript-runtime.md)