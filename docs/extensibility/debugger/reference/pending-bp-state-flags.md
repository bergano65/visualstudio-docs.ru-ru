---
title: PENDING_BP_STATE_FLAGS | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PENDING_BP_STATE_FLAGS
helpviewer_keywords:
- PENDING_BP_STATE_FLAGS enumeration
ms.assetid: 85522449-3fd8-4da5-b0fe-a43160e0c33b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7614b0633f6490e8c3bb6837ed89fda67575c71e
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56691505"
---
# <a name="pendingbpstateflags"></a>PENDING_BP_STATE_FLAGS
Задает флаги состояния ожидающая точка останова.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_PENDING_BP_STATE_FLAGS { 
   PBPSF_NONE        = 0x0000,
   PBPSF_VIRTUALIZED = 0x0001
};
typedef DWORD PENDING_BP_STATE_FLAGS;
```

```csharp
public enum enum_PENDING_BP_STATE_FLAGS { 
   PBPSF_NONE        = 0x0000,
   PBPSF_VIRTUALIZED = 0x0001
};
```

## <a name="members"></a>Участники
 Заполнитель PBPSF_NONE.

 PBPSF_VIRTUALIZED приведены виртуализированных ожидающие точки останова, который необходимо привязать каждый раз при загрузке нового кода.

## <a name="remarks"></a>Примечания
 Используется для `flags` членом [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) структуры.

## <a name="requirements"></a>Требования
 Header: msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)