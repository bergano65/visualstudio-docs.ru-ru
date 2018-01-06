---
title: "PROVIDER_PROCESS_DATA | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PROVIDER_PROCESS_DATA
helpviewer_keywords: PROVIDER_PROCESS_DATA structure
ms.assetid: ec2362ed-4a0c-4a09-9d66-8ff04e4f41ee
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 57b4b23f9bc723ee1ce7a10d12eb9fee0355d8ef
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
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