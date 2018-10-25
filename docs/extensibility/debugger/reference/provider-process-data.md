---
title: PROVIDER_PROCESS_DATA | Документация Майкрософт
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
ms.openlocfilehash: 789385ae229214beeb6c2ab9be90a964127e5e13
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49819736"
---
# <a name="providerprocessdata"></a>PROVIDER_PROCESS_DATA
Эта структура предоставляет сведения о процессах, запущенных на компьютере.  
  
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
 [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md)   
 [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md)   
 [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)