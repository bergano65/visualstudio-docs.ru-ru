---
title: PROCESS_INFO_FIELDS Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FIELDS
helpviewer_keywords:
- PROCESS_INFO_FIELDS enumeration
ms.assetid: 0d9cc345-3d3a-44d8-ae15-a67acb97a828
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f81709e7146bbdef13daa3564bb784fd9c08d58e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714011"
---
# <a name="process_info_fields"></a>PROCESS_INFO_FIELDS
Указано, какую информацию получить для процесса.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_PROCESS_INFO_FIELDS { 
   PIF_FILE_NAME             = 0x00000001,
   PIF_BASE_NAME             = 0x00000002,
   PIF_TITLE                 = 0x00000004,
   PIF_PROCESS_ID            = 0x00000008,
   PIF_SESSION_ID            = 0x00000010,
   PIF_ATTACHED_SESSION_NAME = 0x00000020,
   PIF_CREATION_TIME         = 0x00000040,
   PIF_FLAGS                 = 0x00000080,
   PIF_ALL                   = 0x000000ff
};
typedef DWORD PROCESS_INFO_FIELDS;
```

```csharp
public enum enum_PROCESS_INFO_FIELDS { 
   PIF_FILE_NAME             = 0x00000001,
   PIF_BASE_NAME             = 0x00000002,
   PIF_TITLE                 = 0x00000004,
   PIF_PROCESS_ID            = 0x00000008,
   PIF_SESSION_ID            = 0x00000010,
   PIF_ATTACHED_SESSION_NAME = 0x00000020,
   PIF_CREATION_TIME         = 0x00000040,
   PIF_FLAGS                 = 0x00000080,
   PIF_ALL                   = 0x000000ff
};
```

## <a name="fields"></a>Поля
 `PIF_FILE_NAME`\
 Инициализация/использование `bstrFileName` поля [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) структуры.

 `PIF_BASE_NAME`\
 Инициализация/использование `bstrBaseName` `PROCESS_INFO` поля структуры.

 `PIF_TITLE`\
 Инициализация/использование `bstrTitle` `PROCESS_INFO` поля структуры.

 `PIF_PROCESS_ID`\
 Инициализация/использование `ProcessId` `PROCESS_INFO` поля структуры.

 `PIF_SESSION_ID`\
 Инициализация/использование `dwSessionId` `PROCESS_INFO` поля структуры.

 `PIF_ATTACHED_SESSION_NAME`\
 Инициализация/использование `bstrAttachedSessionName` `PROCESS_INFO` поля структуры.

 `PIF_CREATION_TIME`\
 Инициализация/использование `CreationTime` `PROCESS_INFO` поля структуры.

 `PIF_FLAGS`\
 Инициализация/использование `Flags` `PROCESS_INFO` поля структуры.

 `PIF_ALL`\
 Заполняет все поля.

## <a name="remarks"></a>Примечания
 Прошел в метод [GetInfo,](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) чтобы указать, какие поля [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) структуры должны быть инициализированы.

 Также используется `Fields` в `PROCESS_INFO` поле структуры, чтобы указать, какие поля используются и действительны.

 Эти флаги могут быть `OR`объединены с bitwise .

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
