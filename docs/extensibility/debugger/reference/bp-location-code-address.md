---
title: BP_LOCATION_CODE_ADDRESS | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- BP_LOCATION_CODE_ADDRESS
helpviewer_keywords:
- BP_LOCATION_CODE_ADDRESS structure
ms.assetid: 83c9da8b-19d9-4be5-b225-854543654901
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: df95424ab949baeac93a993dd03c99eeae1e1127
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54966404"
---
# <a name="bplocationcodeaddress"></a>BP_LOCATION_CODE_ADDRESS
Описывает расположение точки останова по адресу в коде.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
typedef struct _BP_LOCATION_CODE_ADDRESS {   
   BSTR bstrContext;  
   BSTR bstrModuleUrl;  
   BSTR bstrFunction;  
   BSTR bstrAddress;  
} BP_LOCATION_CODE_ADDRESS;  
```  
  
## <a name="members"></a>Участники  
 `bstrContext`  
 Контекст точки останова, обычно имя метода или функции материал в стеке вызовов.  
  
 `bstrModuleUrl`  
 URL-адрес модуля, содержащего точку останова.  
  
 `bstrFunction`  
 Имя функции, содержащей точку останова.  
  
 `bstrAddress`  
 Адрес точки останова, который анализируется с вычислитель выражений, чтобы привязать его к [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) объекта.  
  
## <a name="remarks"></a>Примечания  
 Эта структура является членом [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) структуру как часть объединения.  
  
## <a name="requirements"></a>Требования  
 Header: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)