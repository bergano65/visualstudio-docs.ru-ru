---
title: PROCESS_INFO | Документация Майкрософт
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80713887"
---
# <a name="process_info"></a>PROCESS_INFO
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
 `Fields`\
 Сочетание флагов из перечисления [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) , которые указывают, какие поля заполняются.

 `bstrFileName`\
 Полное имя пути процесса. Эквивалентно вызову метода [Зовите](../../../extensibility/debugger/reference/idebugprocess2-getname.md) с параметром `GN_FILENAME` .

 `bstrBaseName`\
 Имя и расширение файла процесса. Эквивалентно вызову `IDebugProcess2::Getname` метода с параметром `GN_BASENAME` .

 `bstrTitle`\
 Заголовок процесса, если он существует. Эквивалентно вызову `IDebugProcess2::Getname` метода с параметром `GN_TITLE` .

 `ProcessId`\
 Структура [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) , идентифицирующая процесс. Эквивалентно вызову метода [жетфисикалпроцессид](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md) .

 `dwSessionId`\
 Идентификатор сеанса отладки, в котором выполняется этот процесс.

 `bstrAttachedSessionName`\
 Имя присоединенного сеанса. Эквивалентно вызову метода [жетаттачедсессионнаме](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md) .

 `CreationTime`\
 Время создания процесса.

 `Flags`\
 Сочетание флагов из перечисления [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md) , определяющих свойства процесса.

## <a name="remarks"></a>Remarks
 Эта структура передается в метод " [info](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) ", где он заполняется.

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)
- [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)
- [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)
- [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)
- [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)
