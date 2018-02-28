---
title: "Функция JsIsRuntimeExecutionDisabled | Документы Майкрософт"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsIsRuntimeExecutionDisabled
helpviewer_keywords:
- JsIsRuntimeExecutionDisabled function
ms.assetid: 77490280-fb84-4614-a1f0-6ac31e3bd607
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f4827205a33d337445faf9b0e9812133f0de3e97
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="jsisruntimeexecutiondisabled-function"></a>Функция JsIsRuntimeExecutionDisabled
Возвращает значение, указывающее, отключено ли в среде выполнения выполнение скрипта.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
STDAPI_(JsErrorCode) JsIsRuntimeExecutionDisabled(    _In_ JsRuntimeHandle runtime,    _Out_ bool *isDisabled);  
```  
  
#### <a name="parameters"></a>Параметры  
 `runtime`  
 Задает среду выполнения, чтобы проверить, отключено ли выполнение.  
  
 `isDisabled`  
 Значение `true`, если выполнение отключено; в противном случае — значение `false`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение `JsNoError`, если операция завершена успешно; в противном случае — код сбоя.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jsrt.h  
  
## <a name="see-also"></a>См. также  
 [Справочник (среда выполнения JavaScript)](../chakra-hosting/reference-javascript-runtime.md)