---
title: PROVIDER_PROCESS_DATA | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROVIDER_PROCESS_DATA
helpviewer_keywords:
- PROVIDER_PROCESS_DATA structure
ms.assetid: ec2362ed-4a0c-4a09-9d66-8ff04e4f41ee
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5845ce7f512a24d341f73afa9f9905339dda87cb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99922977"
---
# <a name="provider_process_data"></a>PROVIDER_PROCESS_DATA
Эта структура предоставляет сведения о процессах, выполняемых на компьютере.

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

## <a name="members"></a>Члены
 `Fields`\
 Сочетание флагов из перечисления [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md) , указывающее, какие поля заполняются.

 `ProgramNodes`\
 Структура [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md) , содержащая массив узлов программы.

 `fIsDebuggerPresent`\
 Ненулевое `TRUE` значение () [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] , если отладчик работает, ноль (), если это не так `FALSE` .

## <a name="remarks"></a>Remarks
 Эта структура передается в метод [жетпровидерпроцессдата](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) , где она заполнена.

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md)
- [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md)
- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)
