---
title: PROCESS_INFO_FLAGS | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FLAGS
helpviewer_keywords:
- PROCESS_INFO_FLAGS enumeration
ms.assetid: 696951ce-701a-40c2-ac8c-b897f3aae6e2
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 88ff2a1da1f937fd4011932979bd95057eb40dfd
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58992189"
---
# <a name="processinfoflags"></a>PROCESS_INFO_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Описывающие или определяющие свойств процесса.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 Указывает, что отладка процесса с помощью отладчика. Возможно, она [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] отладчика, или он может быть некоторые другие отладчика, например, WinDbg.  
  
 PIFLAG_PROCESS_STOPPED  
 Указывает, что процесс будет остановлен. Действительно, только если `PIFLAG_DEBUGGER_ATTACHED` также указан. В [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] и более поздних версий.  
  
 PIFLAG_PROCESS_RUNNING  
 Указывает, что процесс выполняется. Действительно, только если `PIFLAG_DEBUGGER_ATTACHED` также указан. В [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] и более поздних версий.  
  
## <a name="remarks"></a>Примечания  
 Используется для `Flags` членом [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) структуры.  
  
 Эти флаги могут быть объединены с побитовым объектом `OR`.  
  
## <a name="requirements"></a>Требования  
 Header: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
