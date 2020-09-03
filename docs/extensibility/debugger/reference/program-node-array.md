---
title: PROGRAM_NODE_ARRAY | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROGRAM_NODE_ARRAY
helpviewer_keywords:
- PROGRAM_NODE_ARRAY structure
ms.assetid: 8eeea600-eda5-4b7c-868a-0b86d177b0a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ce84fec7a0d9223575828da105e46f43cc6cab09
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80713800"
---
# <a name="program_node_array"></a>PROGRAM_NODE_ARRAY
Содержит массив объектов, описывающих интересующие программы.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct tagPROGRAM_NODE_ARRAY {
   DWORD                dwCount;
   IDebugProgramNode2** Members;
} PROGRAM_NODE_ARRAY;
```

```csharp
public struct tagPROGRAM_NODE_ARRAY {
   public uint                 dwCount;
   public IDebugProgramNode2[] Members;
}
```

## <a name="members"></a>Участники
 `dwCount`\
 Количество объектов в `Members` массиве.

 `Members`\
 Массив объектов [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) , описывающих запрошенные программы.

## <a name="remarks"></a>Remarks
 Эта структура является частью структуры [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) , которая, в свою очередь, заполняется вызовом метода [жетпровидерпроцессдата](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) .

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)
