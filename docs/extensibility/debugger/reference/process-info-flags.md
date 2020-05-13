---
title: PROCESS_INFO_FLAGS Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FLAGS
helpviewer_keywords:
- PROCESS_INFO_FLAGS enumeration
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 36c4cbbe17a109eacd69b76500e8c10d21d2d554
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713963"
---
# <a name="process_info_flags"></a>PROCESS_INFO_FLAGS

Описывает или определяет свойства процесса.

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

## <a name="fields"></a>Поля

`PIFLAG_SYSTEM_PROCESS`\
Означает, что процесс является системным процессом.

`PIFLAG_DEBUGGER_ATTACHED`\
Означает, что процесс отлажен отладчиком. Это может [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] быть отладчик, или это может быть какой-то другой отладчик, например, WinDbg.

`PIFLAG_PROCESS_STOPPED`\
Означает, что процесс остановлен. Действительно только `PIFLAG_DEBUGGER_ATTACHED` в том случае, если также указано. Доступно в Visual Studio 2005 и позже.

`PIFLAG_PROCESS_RUNNING`\
Означает, что процесс запущен. Действительно только `PIFLAG_DEBUGGER_ATTACHED` в том случае, если также указано. Доступно в Visual Studio 2005 и позже.

## <a name="remarks"></a>Примечания

Используется для `Flags` члена [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) структуры.

Эти флаги могут быть `OR`объединены с bitwise .

## <a name="requirements"></a>Требования

Заголовок: msdbg.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также

- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
