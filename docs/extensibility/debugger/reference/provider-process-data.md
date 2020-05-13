---
title: PROVIDER_PROCESS_DATA Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROVIDER_PROCESS_DATA
helpviewer_keywords:
- PROVIDER_PROCESS_DATA structure
ms.assetid: ec2362ed-4a0c-4a09-9d66-8ff04e4f41ee
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bdaf15d09af3199d026155cf7667f063f5bbe858
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713781"
---
# <a name="provider_process_data"></a>PROVIDER_PROCESS_DATA
Эта структура предоставляет информацию о процессах, работающих на машине.

## <a name="syntax"></a>Синтаксис

```cpp
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
 `Fields`\
 Комбинация флагов из [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md) перечисления, указывающие, какие поля заполнены.

 `ProgramNodes`\
 Структура [PROGRAM_NODE_ARRAY,](../../../extensibility/debugger/reference/program-node-array.md) содержащая массив узла программы.

 `fIsDebuggerPresent`\
 Nonzero`TRUE`( ), [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] если отладчик работает, ноль (`FALSE`), если это не так.

## <a name="remarks"></a>Примечания
 Эта структура передается методу [GetProviderProcessData,](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) где она заполняется.

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md)
- [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md)
- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)
