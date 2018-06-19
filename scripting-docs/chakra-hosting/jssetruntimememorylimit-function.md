---
title: Функция JsSetRuntimeMemoryLimit | Документы Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- jsrt/JsSetRuntimeMemoryLimit
helpviewer_keywords:
- JsSetRuntimeMemoryLimit function
ms.assetid: 74feb31f-19f6-43e3-b117-0694c59ac593
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 587eb369e6971c7527177624ccf5baf839246cf9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568974"
---
# <a name="jssetruntimememorylimit-function"></a>Функция JsSetRuntimeMemoryLimit
Задает текущий лимит памяти для среды выполнения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
STDAPI_(JsErrorCode) JsSetRuntimeMemoryLimit(  
   _In_ JsRuntimeHandle runtime,  
   _In_ size_t memoryLimit  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `runtime`  
 Среда выполнения, лимит памяти которой необходимо задать.  
  
 `memoryLimit`  
 Новый лимит среды выполнения в байтах или -1, если лимит памяти отсутствует.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Код `JsNoError` , если операция завершилась успешно, если нет, то код сбоя.  
  
## <a name="remarks"></a>Примечания  
 Если лимит памяти установлен, любая операция, превышающая этот лимит, будет завершаться ошибкой с сообщением «Недостаточно памяти». Если задано значение -1 для лимита памяти среды выполнения, это означает, что у среды выполнения нет лимита памяти. По умолчанию новые среды выполнения не имеют лимита памяти. Если новый лимит памяти превышает текущее использование, вызов будет выполнен успешно, а любые дальнейшие выделения в этой среде выполнения будут завершаться ошибкой до тех пор, пока показатели использования памяти среды выполнения не опустятся ниже лимита.  
  
 Можно всегда задать лимит памяти среды выполнения независимо от того, является ли среда выполнения активной в другом потоке.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jsrt.h  
  
## <a name="see-also"></a>См. также  
 [Справочник (среда выполнения JavaScript)](../chakra-hosting/reference-javascript-runtime.md)