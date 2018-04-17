---
title: PROVIDER_PROCESS_DATA | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- PROVIDER_PROCESS_DATA
helpviewer_keywords:
- PROVIDER_PROCESS_DATA structure
ms.assetid: ec2362ed-4a0c-4a09-9d66-8ff04e4f41ee
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 61b1b5d67faea0ce5c1c2a56b3f411cd4f947067
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="providerprocessdata"></a>PROVIDER_PROCESS_DATA
Эта структура содержит сведения о процессах, запущенных на компьютере.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
typedef struct tagPROVIDER_PROCESS_DATA {  
   PROVIDER_FIELDS    Fields;  
   PROGRAM_NODE_ARRAY ProgramNodes;  
   BOOL               fIsDebuggerPresent;  
} PROVIDER_PROCESS_DATA;  
```  
  
```csharp  
public struct PROVIDER_PROCESS_DATA {  
   public uint               Fields;  
   public PROGRAM_NODE_ARRAY ProgramNodes;  
   public int                fIsDebuggerPresent;  
}  
```  
  
## <a name="members"></a>Участники  
 Поля  
 Сочетание флагов из [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md) перечисления, указывающее, какие поля заполнены.  
  
 ProgramNodes  
 Объект [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md) структуру, содержащую массив узлов программы.  
  
 fIsDebuggerPresent  
 Ненулевое значение (`TRUE`) Если [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] работы отладчика, ноль (`FALSE`) Если это не так.  
  
## <a name="remarks"></a>Примечания  
 Эта структура передается [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) метод, где он заполняется.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Структур и объединений](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md)   
 [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md)   
 [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)