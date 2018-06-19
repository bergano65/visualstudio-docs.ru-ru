---
title: Функция JsDisableRuntimeExecution | Документы Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- jsrt/JsDisableRuntimeExecution
helpviewer_keywords:
- JsDisableRuntimeExecution function
ms.assetid: 4bd4670a-a9da-4f8c-b3fd-1fd366d915c3
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f44545f7c81344a2d22f0083087f77ac8074278c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568274"
---
# <a name="jsdisableruntimeexecution-function"></a>Функция JsDisableRuntimeExecution
Приостанавливает выполнение скрипта и завершает выполнение всех выполняемых скриптов в среде выполнения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
STDAPI_(JsErrorCode) JsDisableRuntimeExecution(  
   _In_ JsRuntimeHandle runtime  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `runtime`  
 Приостанавливаемая среда выполнения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Код `JsNoError` , если операция завершилась успешно, если нет, то код сбоя.  
  
## <a name="remarks"></a>Примечания  
 Вызовы, адресованные приостановленной среде выполнения, будут завершаться сбоем до вызова метода `JsEnableRuntimeExecution`.  
  
 Этот API не обязательно вызывать в потоке, где активна среда выполнения. Несмотря на то что среда выполнения будет приведена в приостановленное состояние, выполняемый скрипт не будет приостановлен немедленно; выполнение скрипта будет, как только возможно, завершено с неперехватываемым исключением.  
  
 Приостановка выполнения в среде выполнения, которая уже приостановлена, является холостой.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jsrt.h  
  
## <a name="see-also"></a>См. также  
 [Справочник (среда выполнения JavaScript)](../chakra-hosting/reference-javascript-runtime.md)