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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205056"
---
# <a name="process_info_flags"></a>PROCESS_INFO_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Описывает или задает свойства процесса.  
  
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
 Указывает, что процесс является системным процессом.  
  
 PIFLAG_DEBUGGER_ATTACHED  
 Указывает, что процесс отлаживается отладчиком. Это может быть [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] отладчик или некоторый другой отладчик, например WinDbg.  
  
 PIFLAG_PROCESS_STOPPED  
 Указывает, что процесс остановлен. Допустимо, только если `PIFLAG_DEBUGGER_ATTACHED` также указано значение. Доступно в [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] и более поздних версиях.  
  
 PIFLAG_PROCESS_RUNNING  
 Указывает, что процесс выполняется. Допустимо, только если `PIFLAG_DEBUGGER_ATTACHED` также указано значение. Доступно в [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] и более поздних версиях.  
  
## <a name="remarks"></a>Remarks  
 Используется для `Flags` элемента структуры [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) .  
  
 Эти флаги можно сочетать с помощью побитовой операции `OR` .  
  
## <a name="requirements"></a>Требования  
 Заголовок: мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
