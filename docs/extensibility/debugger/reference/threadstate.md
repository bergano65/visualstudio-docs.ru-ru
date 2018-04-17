---
title: THREADSTATE | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- THREADSTATE
helpviewer_keywords:
- THREADSTATE enumeration
ms.assetid: 62efdd7c-25b1-4fd3-9d06-ac1830a418a9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a5a2153b6f97727cbf436c66686160cece15c287
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="threadstate"></a>THREADSTATE
Указывает состояние потока.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_THREADSTATE {   
   THREADSTATE_RUNNING = 0x0001,  
   THREADSTATE_STOPPED = 0x0002,  
   THREADSTATE_FRESH   = 0x0003,  
   THREADSTATE_DEAD    = 0x0004,  
   THREADSTATE_FROZEN  = 0x0005  
};  
typedef DWORD THREADSTATE;  
```  
  
```csharp  
public enum enum_THREADSTATE {   
   THREADSTATE_RUNNING = 0x0001,  
   THREADSTATE_STOPPED = 0x0002,  
   THREADSTATE_FRESH   = 0x0003,  
   THREADSTATE_DEAD    = 0x0004,  
   THREADSTATE_FROZEN  = 0x0005  
};  
```  
  
## <a name="members"></a>Участники  
 THREADSTATE_RUNNING  
 Указывает, что поток выполняется.  
  
 THREADSTATE_STOPPED  
 Указывает, что поток остановлен из-за точки останова.  
  
 THREADSTATE_FRESH  
 Указывает, что поток был создан, но еще не запущен код.  
  
 THREADSTATE_DEAD  
 Указывает, что поток бездействует.  
  
 THREADSTATE_FROZEN  
 Указывает, что поток заморожен (выполнение не может выполняться).  
  
## <a name="remarks"></a>Примечания  
 Используется для `dwThreadState` поле [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) структуры.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)