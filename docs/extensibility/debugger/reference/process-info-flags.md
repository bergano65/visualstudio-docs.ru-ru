---
title: "PROCESS_INFO_FLAGS | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PROCESS_INFO_FLAGS
helpviewer_keywords:
- PROCESS_INFO_FLAGS enumeration
ms.assetid: 696951ce-701a-40c2-ac8c-b897f3aae6e2
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 9ff1df7e73c8f09934504552f33d7f9ce4c537e4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="processinfoflags"></a>PROCESS_INFO_FLAGS
Описывает или задание свойств процесса.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_PROCESS_INFO_FLAGS {   
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,  
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,  
   PIFLAG_PROCESS_STOPPED   = 0x00000004,  
   PIFLAG_PROCESS_RUNNING   = 0x00000008,  
};  
typedef DWORD PROCESS_INFO_FLAGS;  
```  
  
```csharp  
enum enum_PROCESS_INFO_FLAGS {   
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
 Указывает, что процесс остановлен. Только если `PIFLAG_DEBUGGER_ATTACHED` также указан. Доступные в [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)] и более поздних версий.  
  
 PIFLAG_PROCESS_RUNNING  
 Указывает, что процесс выполняется. Только если `PIFLAG_DEBUGGER_ATTACHED` также указан. Доступные в [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)] и более поздних версий.  
  
## <a name="remarks"></a>Примечания  
 Используется для `Flags` членом [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) структуры.  
  
 Эти флаги могут объединяться с битовой `OR`.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)