---
title: AD_PROCESS_ID_TYPE | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- AD_PROCESS_ID_TYPE
helpviewer_keywords:
- AD_PROCESS_ID_TYPE enumeration
ms.assetid: 0aab80e9-285a-4697-94ac-c864d42a6aaa
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f27791b555d2f18e1e0a338bbfb5893f9047fd4e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53819604"
---
# <a name="adprocessidtype"></a>AD_PROCESS_ID_TYPE
Указывает способ интерпретации идентификатора процесса в [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) структуры.  
  
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
 Идентификатор процесса представляет собой идентификатор GUID. Используйте `ProcessId.guidProcessId` поле `AD_PROCESS_ID` структуры.  
  
## <a name="remarks"></a>Примечания  
 Используется для `ProcessIdType` членом [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) структура, определяющая тип идентификатор процесса, который содержится в структуре. Определяет способ интерпретации `ProcessId` объединения в структуре.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)