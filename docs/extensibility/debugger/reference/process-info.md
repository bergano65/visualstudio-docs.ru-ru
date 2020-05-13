---
title: PROCESS_INFO Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO
helpviewer_keywords:
- PROCESS_INFO structure
ms.assetid: 260c33cc-a05e-4645-84b6-536d0b3b0537
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ef73145fb0a2598dc5e4ee98e8652314e0bc1c89
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713887"
---
# <a name="process_info"></a>PROCESS_INFO
Содержит информацию о процессе.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct tagPROCESS_INFO { 
   PROCESS_INFO_FIELDS Fields;
   BSTR                bstrFileName;
   BSTR                bstrBaseName;
   BSTR                bstrTitle;
   AD_PROCESS_ID       ProcessId;
   DWORD               dwSessionId;
   BSTR                bstrAttachedSessionName;
   FILETIME            CreationTime;
   PROCESS_INFO_FLAGS  Flags;
} PROCESS_INFO;
```

```csharp
public struct PROCESS_INFO { 
   public uint          Fields;
   public string        bstrFileName;
   public string        bstrBaseName;
   public string        bstrTitle;
   public AD_PROCESS_ID ProcessId;
   public uint          dwSessionId;
   public string        bstrAttachedSessionName;
   public FILETIME      CreationTime;
   public uint          Flags;
};
```

## <a name="members"></a>Участники
 `Fields`\
 Комбинация флагов [из PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) перечисления, которые определяют, какие поля заполнены.

 `bstrFileName`\
 Полное название пути процесса. Эквивалент вызову метода [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) с параметром. `GN_FILENAME`

 `bstrBaseName`\
 Имя файла и расширение процесса. Эквивалент вызову `IDebugProcess2::Getname` метода `GN_BASENAME`с параметром.

 `bstrTitle`\
 Название процесса, если он существует. Эквивалент вызову `IDebugProcess2::Getname` метода `GN_TITLE`с параметром.

 `ProcessId`\
 [Структура AD_PROCESS_ID,](../../../extensibility/debugger/reference/ad-process-id.md) которая определяет процесс. Эквивалент вызова метода [GetPhysicalProcessId.](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)

 `dwSessionId`\
 Идентификатор сеанса отладки, в который находится этот процесс.

 `bstrAttachedSessionName`\
 Прилагаемое имя сеанса. Эквивалент вызова метода [GetAttachedSessionName.](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)

 `CreationTime`\
 Время создания процесса.

 `Flags`\
 Комбинация флагов [из PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md) перечисления, которые определяют свойства процесса.

## <a name="remarks"></a>Примечания
 Эта структура передается методу [GetInfo,](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) где она заполняется.

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)
- [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)
- [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)
- [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)
- [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)
