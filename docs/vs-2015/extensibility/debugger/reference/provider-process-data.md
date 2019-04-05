---
title: PROVIDER_PROCESS_DATA | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- PROVIDER_PROCESS_DATA
helpviewer_keywords:
- PROVIDER_PROCESS_DATA structure
ms.assetid: ec2362ed-4a0c-4a09-9d66-8ff04e4f41ee
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 89192d814ccee3dd2a134807d8ce01880689d951
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58981073"
---
# <a name="providerprocessdata"></a>PROVIDER_PROCESS_DATA
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Эта структура предоставляет сведения о процессах, запущенных на компьютере.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
typedef struct tagPROVIDER_PROCESS_DATA {  
   PROVIDER_FIELDS    Fields;  
   PROGRAM_NODE_ARRAY ProgramNodes;  
   BOOL               fIsDebuggerPresent;  
} PROVIDER_PROCESS_DATA;  
```  
  
```csharp  
public struct PROVIDER_PROCESS_DATA {  
   public uint               Fields;  
   public PROGRAM_NODE_ARRAY ProgramNodes;  
   public int                fIsDebuggerPresent;  
}  
```  
  
## <a name="members"></a>Участники  
 Поля  
 Сочетание флагов из [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md) перечисления, указывающее, какие поля заполнены.  
  
 ProgramNodes  
 Объект [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md) структуру, содержащую массив узлов программы.  
  
 fIsDebuggerPresent  
 Ненулевое значение (`TRUE`) Если [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] работы отладчика, ноль (`FALSE`) Если это не так.  
  
## <a name="remarks"></a>Примечания  
 Эта структура передается [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) метод, где он заполняется.  
  
## <a name="requirements"></a>Требования  
 Header: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md)   
 [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md)   
 [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)
