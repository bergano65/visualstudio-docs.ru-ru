---
title: AD_PROCESS_ID_TYPE | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AD_PROCESS_ID_TYPE
helpviewer_keywords:
- AD_PROCESS_ID_TYPE enumeration
ms.assetid: 0aab80e9-285a-4697-94ac-c864d42a6aaa
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 405d11b0c685017d59251ba83126a73fe1a96db2
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56708970"
---
# <a name="adprocessidtype"></a>AD_PROCESS_ID_TYPE
Указывает способ интерпретации идентификатора процесса в [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) структуры.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_AD_PROCESS_ID {
    AD_PROCESS_ID_SYSTEM = 0,
    AD_PROCESS_ID_GUID   = 1
};
typedef DWORD AD_PROCESS_ID_TYPE;
```

```csharp
public enum enum_AD_PROCESS_ID {
    AD_PROCESS_ID_SYSTEM = 0,
    AD_PROCESS_ID_GUID   = 1
};
```

## <a name="members"></a>Участники
Идентификатор процесса AD_PROCESS_ID_SYSTEM — это идентификатор системы. Используйте `ProcessId.dwProcessId` поле [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) структуры.

Идентификатор процесса AD_PROCESS_ID_GUID представляет собой идентификатор GUID. Используйте `ProcessId.guidProcessId` поле `AD_PROCESS_ID` структуры.

## <a name="remarks"></a>Примечания
Используется для `ProcessIdType` членом [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) структура, определяющая тип идентификатор процесса, который содержится в структуре. Определяет способ интерпретации `ProcessId` объединения в структуре.

## <a name="requirements"></a>Требования
Header: msdbg.h

Пространство имен: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
