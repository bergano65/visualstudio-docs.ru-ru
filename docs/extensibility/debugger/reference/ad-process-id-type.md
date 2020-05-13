---
title: AD_PROCESS_ID_TYPE Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AD_PROCESS_ID_TYPE
helpviewer_keywords:
- AD_PROCESS_ID_TYPE enumeration
ms.assetid: 0aab80e9-285a-4697-94ac-c864d42a6aaa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a88fbe97cede8d343f1a96bc1917a69b8905b02b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738187"
---
# <a name="ad_process_id_type"></a>AD_PROCESS_ID_TYPE
Определяет, как интерпретировать идентификатор процесса в [структуре AD_PROCESS_ID.](../../../extensibility/debugger/reference/ad-process-id.md)

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

## <a name="fields"></a>Поля
`AD_PROCESS_ID_SYSTEM`\
Идентификатор процесса — это идентификатор системы. Используйте `ProcessId.dwProcessId` поле [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) структуры.

`AD_PROCESS_ID_GUID`\
Идентификатор процесса — это GUID. Используйте `ProcessId.guidProcessId` поле `AD_PROCESS_ID` структуры.

## <a name="remarks"></a>Примечания
Используется для `ProcessIdType` AD_PROCESS_ID [структуры](../../../extensibility/debugger/reference/ad-process-id.md) для определения типа идентификатора процесса, содержащегося в структуре. Определяет, как интерпретировать `ProcessId` союз в структуре.

## <a name="requirements"></a>Требования
Заголовок: msdbg.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
