---
title: PROCESS_INFO_FLAGS | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- PROCESS_INFO_FLAGS
helpviewer_keywords:
- PROCESS_INFO_FLAGS enumeration
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0c7d319d2053cfa67bd4e7fe77c68474fceb03a2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53896127"
---
# <a name="processinfoflags"></a>PROCESS_INFO_FLAGS

Описывающие или определяющие свойств процесса.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_PROCESS_INFO_FLAGS { 
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,
   PIFLAG_PROCESS_STOPPED   = 0x00000004,
   PIFLAG_PROCESS_RUNNING   = 0x00000008,
};
typedef DWORD PROCESS_INFO_FLAGS;
```

```csharp
enum enum_PROCESS_INFO_FLAGS { 
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,
   PIFLAG_PROCESS_STOPPED   = 0x00000004,
   PIFLAG_PROCESS_RUNNING   = 0x00000008,
};
```

## <a name="members"></a>Участники

PIFLAG_SYSTEM_PROCESS  
Указывает, что процесс — это системный процесс.

PIFLAG_DEBUGGER_ATTACHED  
Указывает, что отладка процесса с помощью отладчика. Возможно, она [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] отладчика, или он может быть некоторые другие отладчика, например, WinDbg.

PIFLAG_PROCESS_STOPPED  
Указывает, что процесс будет остановлен. Действительно, только если `PIFLAG_DEBUGGER_ATTACHED` также указан. В Visual Studio 2005 и более поздних версий.

PIFLAG_PROCESS_RUNNING  
Указывает, что процесс выполняется. Действительно, только если `PIFLAG_DEBUGGER_ATTACHED` также указан. В Visual Studio 2005 и более поздних версий.

## <a name="remarks"></a>Примечания

Используется для `Flags` членом [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) структуры.

Эти флаги могут быть объединены с побитовым объектом `OR`.

## <a name="requirements"></a>Требования

Заголовок: msdbg.h

Пространство имен: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также

[Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)  
[PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)