---
title: PROVIDER_FLAGS | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROVIDER_FLAGS
helpviewer_keywords:
- PROVIDER_FLAGS enumeration
ms.assetid: 8cbd2312-ed2f-4477-b192-c3f25c6098c3
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 803d9569c611e3c4cd70f2c82ecd525716d8ddb3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62913531"
---
# <a name="providerflags"></a>PROVIDER_FLAGS
Задает требуемые свойства должны быть получены от поставщика программы.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_PROVIDER_FLAGS {
   PFLAG_NONE                    = 0x00,
   PFLAG_REMOTE_PORT             = 0x01,
   PFLAG_DEBUGGEE                = 0x02,
   PFLAG_ATTACHED_TO_DEBUGGEE    = 0x04,
   PFLAG_REASON_WATCH            = 0x08,
   PFLAG_GET_PROGRAM_NODES       = 0x10,
   PFLAG_GET_IS_DEBUGGER_PRESENT = 0x20
};
typedef DWORD PROVIDER_FLAGS;
```

```csharp
public enum enum_PROVIDER_FLAGS {
   PFLAG_NONE                    = 0x00,
   PFLAG_REMOTE_PORT             = 0x01,
   PFLAG_DEBUGGEE                = 0x02,
   PFLAG_ATTACHED_TO_DEBUGGEE    = 0x04,
   PFLAG_REASON_WATCH            = 0x08,
   PFLAG_GET_PROGRAM_NODES       = 0x10,
   PFLAG_GET_IS_DEBUGGER_PRESENT = 0x20
};
```

## <a name="members"></a>Участники
 Указаны флаги PFLAG_NONE нет.

 Список программ на разных компьютерах вызывающий PFLAG_REMOTE_PORT [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)].

 PFLAG_DEBUGGEE процесс находится в состоянии отладки данным экземпляром класса [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)].

 PFLAG_ATTACH_TODEBUGGEE [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] присоединяется к отлаживаемой программы, но не запускать его.

 PFLAG_REASON_WATCH [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] наблюдении за событиями.

 Вызывающий PFLAG_GET_PROGRAM_NODES `ProgramNodes` поле [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) структуры.

 Вызывающий PFLAG_GET_IS_DEBUGGER_PRESENT `fIsTheDebuggerPresent` поле `PROVIDER_PROCESS_DATA` структуры.

## <a name="remarks"></a>Примечания
 Эти флаги передаются следующие методы:

- [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)

- [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)

- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)

  Эти значения могут объединяться с побитовым объектом `OR`.

## <a name="requirements"></a>Требования
 Header: msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)
- [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)
- [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)
- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)