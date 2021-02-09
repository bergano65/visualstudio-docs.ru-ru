---
title: PROCESS_INFO_FIELDS | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FIELDS
helpviewer_keywords:
- PROCESS_INFO_FIELDS enumeration
ms.assetid: 0d9cc345-3d3a-44d8-ae15-a67acb97a828
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 451a6ea5334006bb23e8961595f4de85c985b8ca
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895951"
---
# <a name="process_info_fields"></a>PROCESS_INFO_FIELDS
Указывает, какой тип сведений необходимо получить для процесса.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_PROCESS_INFO_FIELDS { 
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
public enum enum_PROCESS_INFO_FIELDS { 
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
 Инициализируйте или используйте `bstrFileName` поле структуры [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) .

 `PIF_BASE_NAME`\
 Инициализируйте или используйте `bstrBaseName` поле `PROCESS_INFO` структуры.

 `PIF_TITLE`\
 Инициализируйте или используйте `bstrTitle` поле `PROCESS_INFO` структуры.

 `PIF_PROCESS_ID`\
 Инициализируйте или используйте `ProcessId` поле `PROCESS_INFO` структуры.

 `PIF_SESSION_ID`\
 Инициализируйте или используйте `dwSessionId` поле `PROCESS_INFO` структуры.

 `PIF_ATTACHED_SESSION_NAME`\
 Инициализируйте или используйте `bstrAttachedSessionName` поле `PROCESS_INFO` структуры.

 `PIF_CREATION_TIME`\
 Инициализируйте или используйте `CreationTime` поле `PROCESS_INFO` структуры.

 `PIF_FLAGS`\
 Инициализируйте или используйте `Flags` поле `PROCESS_INFO` структуры.

 `PIF_ALL`\
 Заполняет все поля.

## <a name="remarks"></a>Remarks
 Передается в метод " [info](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) ", чтобы указать, какие поля структуры [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) должны быть инициализированы.

 Также используется в `Fields` поле структуры, `PROCESS_INFO` чтобы указать, какие поля используются и являются допустимыми.

 Эти флаги можно сочетать с помощью побитовой операции `OR` .

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
