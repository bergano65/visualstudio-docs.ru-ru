---
title: Функция JsIdle | Документы Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- jsrt/JsIdle
helpviewer_keywords:
- JsIdle function
ms.assetid: 372d1c62-8e19-4886-aa33-364cabc09bba
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ddffd4f37c0e10985a2dbca26558d8a94b21b2f7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568814"
---
# <a name="jsidle-function"></a>Функция JsIdle
Отдает среде выполнения команду выполнить любую необходимую обработку простоя.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
STDAPI_(JsErrorCode) JsIdle(  
   _Out_opt_ unsigned int *nextIdleTick  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `nextIdleTick`  
 Следующий такт системы при появлении дополнительной работы простоя для выполнения. Может быть равен null. Возвращает максимальное количество тактов при отсутствии работы простоя, которую предстоит выполнить.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Код `JsNoError` , если операция завершилась успешно, если нет, то код сбоя.  
  
## <a name="remarks"></a>Примечания  
 Если обработка простоя включена для текущей среды выполнения, при вызове метода `JsIdle` система информирует текущую среду выполнения, что узел простаивает и среда выполнения может выполнять задачи очистки памяти.  
  
 `JsIdle` также может возвращать число тактов системы до появления дополнительной работы простоя для среды выполнения. При вызове `JsIdle` до истечения этого количества тактов никакая работа выполняться не будет.  
  
 Требуется контекст активного скрипта.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jsrt.h  
  
## <a name="see-also"></a>См. также  
 [Справочник (среда выполнения JavaScript)](../chakra-hosting/reference-javascript-runtime.md)