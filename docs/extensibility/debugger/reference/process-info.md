---
title: PROCESS_INFO | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO
helpviewer_keywords:
- PROCESS_INFO structure
ms.assetid: 260c33cc-a05e-4645-84b6-536d0b3b0537
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a18d9a158e69fd18319f187274a2db7d00e24546
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56720631"
---
# <a name="processinfo"></a>PROCESS_INFO
Содержит сведения о процессе.

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
 Сочетание флагов из поля [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) перечисление, указать, какие поля заполнены.

 bstrFileName полное имя процесса. Аналогичен вызову [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) метод с параметром `GN_FILENAME`.

 bstrBaseName имя файла и расширение процесса. Аналогичен вызову `IDebugProcess2::Getname` метод с параметром `GN_BASENAME`.

 bstrTitle название процесса, если он существует. Аналогичен вызову `IDebugProcess2::Getname` метод с параметром `GN_TITLE`.

 ProcessId [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) структуру, определяющий процесс. Аналогичен вызову [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md) метод.

 dwSessionId идентификатор, на котором этот процесс выполняется в сеанс отладки.

 bstrAttachedSessionName имя вложенного сеанса. Аналогичен вызову [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md) метод.

 CreationTime время создания процесса.

 Флаги сочетание флагов из [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md) перечисления, укажите для свойства процесса.

## <a name="remarks"></a>Примечания
 Эта структура передается [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) метод, где он заполняется.

## <a name="requirements"></a>Требования
 Header: msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)
- [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)
- [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)
- [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)
- [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)