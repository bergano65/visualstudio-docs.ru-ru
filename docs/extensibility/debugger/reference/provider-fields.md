---
title: PROVIDER_FIELDS | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- PROVIDER_FIELDS
helpviewer_keywords:
- PROVIDER_FIELDS enumeration
ms.assetid: 39631545-2b0e-45b4-978b-d63656484b02
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: deda42120dc98e0222910c48b0faf574a57f03dd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31126052"
---
# <a name="providerfields"></a>PROVIDER_FIELDS
Указывает свойства, связанные с поставщиком программы.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_PROVIDER_FIELDS {  
   PFIELD_PROGRAM_NODES       = 0x01,  
   PFIELD_IS_DEBUGGER_PRESENT = 0x02  
};  
typedef DWORD PROVIDER_FIELDS;  
```  
  
```csharp  
public enum enum_PROVIDER_FIELDS {  
   PFIELD_PROGRAM_NODES       = 0x01,  
   PFIELD_IS_DEBUGGER_PRESENT = 0x02  
};  
```  
  
## <a name="members"></a>Участники  
 PFIELD_PROGRAM_NODES  
 `ProgramNodes` Поле допустимо.  
  
 PFIELD_IS_DEBUGGER_PRESENT  
 `fIsDebuggerPresent` Поле допустимо.  
  
## <a name="remarks"></a>Примечания  
 Эти значения возвращаются в `Fields` членом [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) структуры, чтобы указать, какие поля структуры явно были заполнены.  
  
 Эти значения могут быть объединены с помощью битового оператора `OR`.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)