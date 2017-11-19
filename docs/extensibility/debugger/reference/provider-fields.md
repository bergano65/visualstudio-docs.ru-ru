---
title: "PROVIDER_FIELDS | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PROVIDER_FIELDS
helpviewer_keywords: PROVIDER_FIELDS enumeration
ms.assetid: 39631545-2b0e-45b4-978b-d63656484b02
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 01aa9048e26c265b1fe04ba653fb224b86ec77cd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
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
  
## <a name="members"></a>Члены  
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