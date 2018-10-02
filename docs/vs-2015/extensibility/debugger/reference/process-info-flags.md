---
title: PROCESS_INFO_FLAGS | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- PROCESS_INFO_FLAGS
helpviewer_keywords:
- PROCESS_INFO_FLAGS enumeration
ms.assetid: 696951ce-701a-40c2-ac8c-b897f3aae6e2
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5f8bd5fdf7e377e7b43325a49aaa9dc505022cef
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47561538"
---
# <a name="processinfoflags"></a>PROCESS_INFO_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [PROCESS_INFO_FLAGS](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/process-info-flags).  
  
Описывающие или определяющие свойств процесса.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 Указывает, что отладка процесса с помощью отладчика. Возможно, она [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] отладчика, или он может быть некоторые другие отладчика, например, WinDbg.  
  
 PIFLAG_PROCESS_STOPPED  
 Указывает, что процесс будет остановлен. Действительно, только если `PIFLAG_DEBUGGER_ATTACHED` также указан. В [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] и более поздних версий.  
  
 PIFLAG_PROCESS_RUNNING  
 Указывает, что процесс выполняется. Действительно, только если `PIFLAG_DEBUGGER_ATTACHED` также указан. В [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] и более поздних версий.  
  
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

