---
title: "Функция JsSetException | Документы Майкрософт"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsSetException
helpviewer_keywords:
- JsSetException function
ms.assetid: c528793a-2e1b-4ee1-bd2e-e63fd547dc40
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5d8fce71f14dedea02e1809fb72281f575f60604
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="jssetexception-function"></a>Функция JsSetException
Переводит среду выполнения текущего контекста в состояние исключения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
STDAPI_(JsErrorCode) JsSetException(  
   _In_ JsValueRef exception  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `exception`  
 Исключение JavaScript, которое необходимо задать для среды выполнения текущего контекста.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение `JsNoError`, если подсистема не переведена в состояние исключения; в противном случае — код сбоя.  
  
## <a name="remarks"></a>Примечания  
 Если среда выполнения текущего контекста уже находится в состоянии исключения, этот API возвращает значение `JsErrorInExceptionState`.  
  
 Требуется контекст активного скрипта.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jsrt.h  
  
## <a name="see-also"></a>См. также  
 [Справочник (среда выполнения JavaScript)](../chakra-hosting/reference-javascript-runtime.md)