---
title: BP_LOCATION_CODE_ADDRESS | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BP_LOCATION_CODE_ADDRESS
helpviewer_keywords:
- BP_LOCATION_CODE_ADDRESS structure
ms.assetid: 83c9da8b-19d9-4be5-b225-854543654901
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a6d0972b4e326cabd00341db685a0b73c8c104c7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31099126"
---
# <a name="bplocationcodeaddress"></a>BP_LOCATION_CODE_ADDRESS
Описывает местоположение точки останова по адресу в коде.  
  
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
 Контекст точки останова, обычно имя метода или функции по результатам в стеке вызова.  
  
 `bstrModuleUrl`  
 URL-адрес модуля, содержащего точку останова.  
  
 `bstrFunction`  
 Имя функции, которая содержит точку останова.  
  
 `bstrAddress`  
 Адрес точки останова, который анализируется с вычислитель выражений, чтобы привязать его к [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) объекта.  
  
## <a name="remarks"></a>Примечания  
 Эта структура является членом [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) структуру как часть объединения.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Структур и объединений](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)