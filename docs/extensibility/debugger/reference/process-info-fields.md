---
title: "PROCESS_INFO_FIELDS | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PROCESS_INFO_FIELDS
helpviewer_keywords: PROCESS_INFO_FIELDS enumeration
ms.assetid: 0d9cc345-3d3a-44d8-ae15-a67acb97a828
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e5732b287512cb14ab885619799d0c885f69b791
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="processinfofields"></a>PROCESS_INFO_FIELDS
Указанный тип получаемых сведений для процесса.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_PROCESS_INFO_FIELDS {   
   PIF_FILE_NAME             = 0x00000001,  
   PIF_BASE_NAME             = 0x00000002,  
   PIF_TITLE                 = 0x00000004,  
   PIF_PROCESS_ID            = 0x00000008,  
   PIF_SESSION_ID            = 0x00000010,  
   PIF_ATTACHED_SESSION_NAME = 0x00000020,  
   PIF_CREATION_TIME         = 0x00000040,  
   PIF_FLAGS                 = 0x00000080,  
   PIF_ALL                   = 0x000000ff  
};  
typedef DWORD PROCESS_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_PROCESS_INFO_FIELDS {   
   PIF_FILE_NAME             = 0x00000001,  
   PIF_BASE_NAME             = 0x00000002,  
   PIF_TITLE                 = 0x00000004,  
   PIF_PROCESS_ID            = 0x00000008,  
   PIF_SESSION_ID            = 0x00000010,  
   PIF_ATTACHED_SESSION_NAME = 0x00000020,  
   PIF_CREATION_TIME         = 0x00000040,  
   PIF_FLAGS                 = 0x00000080,  
   PIF_ALL                   = 0x000000ff  
};  
```  
  
## <a name="members"></a>Члены  
 PIF_FILE_NAME  
 Инициализация или использовать `bstrFileName` поле [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) структуры.  
  
 PIF_BASE_NAME  
 Инициализация или использовать `bstrBaseName` поле `PROCESS_INFO` структуры.  
  
 PIF_TITLE  
 Инициализация или использовать `bstrTitle` поле `PROCESS_INFO` структуры.  
  
 PIF_PROCESS_ID  
 Инициализация или использовать `ProcessId` поле `PROCESS_INFO` структуры.  
  
 PIF_SESSION_ID  
 Инициализация или использовать `dwSessionId` поле `PROCESS_INFO` структуры.  
  
 PIF_ATTACHED_SESSION_NAME  
 Инициализация или использовать `bstrAttachedSessionName` поле `PROCESS_INFO` структуры.  
  
 PIF_CREATION_TIME  
 Инициализация или использовать `CreationTime` поле `PROCESS_INFO` структуры.  
  
 PIF_FLAGS  
 Инициализация или использовать `Flags` поле `PROCESS_INFO` структуры.  
  
 PIF_ALL  
 Заполнения всех полей.  
  
## <a name="remarks"></a>Примечания  
 Передаваемый [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) метод, чтобы указать, какие поля [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) структуры должны быть инициализированы.  
  
 Также используется в `Fields` поле `PROCESS_INFO` структуры указывает, какие поля используются и допустимым.  
  
 Эти флаги могут объединяться с битовой `OR`.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)