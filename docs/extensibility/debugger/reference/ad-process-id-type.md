---
title: "AD_PROCESS_ID_TYPE | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: AD_PROCESS_ID_TYPE
helpviewer_keywords: AD_PROCESS_ID_TYPE enumeration
ms.assetid: 0aab80e9-285a-4697-94ac-c864d42a6aaa
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 3aa9720b64404eb2478763b36c04addb480babfa
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="adprocessidtype"></a>AD_PROCESS_ID_TYPE
Указывает способ интерпретации идентификатор процесса в [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) структуры.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_AD_PROCESS_ID {  
   AD_PROCESS_ID_SYSTEM = 0,  
   AD_PROCESS_ID_GUID   = 1  
};  
typedef DWORD AD_PROCESS_ID_TYPE;  
```  
  
```csharp  
public enum enum_AD_PROCESS_ID {  
   AD_PROCESS_ID_SYSTEM = 0,  
   AD_PROCESS_ID_GUID   = 1  
};  
```  
  
## <a name="members"></a>Участники  
 AD_PROCESS_ID_SYSTEM  
 Идентификатор процесса — это идентификатор системы. Используйте `ProcessId.dwProcessId` поле [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) структуры.  
  
 AD_PROCESS_ID_GUID  
 Идентификатор процесса — это GUID. Используйте `ProcessId.guidProcessId` поле `AD_PROCESS_ID` структуры.  
  
## <a name="remarks"></a>Примечания  
 Используется для `ProcessIdType` членом [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) структура, определяющая тип идентификатор процесса, который содержится в структуре. Определяет способ интерпретации `ProcessId` объединения в структуре.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)