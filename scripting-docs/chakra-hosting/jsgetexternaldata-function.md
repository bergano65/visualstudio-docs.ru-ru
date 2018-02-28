---
title: "Функция JsGetExternalData | Документы Майкрософт"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsGetExternalData
helpviewer_keywords:
- JsGetExternalData function
ms.assetid: 1919e1da-3ea7-4269-a5fb-a3be06bd029b
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da78672f85159070949d067867699cfb5223b31c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="jsgetexternaldata-function"></a>Функция JsGetExternalData
Извлекает данные из внешнего объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
STDAPI_(JsErrorCode) JsGetExternalData(  
   _In_ JsValueRef object,  
   _Out_ void **externalData  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `object`  
 Внешний объект.  
  
 `externalData`  
 Внешние данные, хранящиеся в объекте. Может иметь значение null, если в объекте не сохранены внешние данные.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Код `JsNoError` , если операция завершилась успешно, если нет, то код сбоя.  
  
## <a name="remarks"></a>Примечания  
 Требуется контекст активного скрипта.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jsrt.h  
  
## <a name="see-also"></a>См. также  
 [Справочник (среда выполнения JavaScript)](../chakra-hosting/reference-javascript-runtime.md)