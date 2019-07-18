---
title: PROCESS_INFO_FIELDS | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FIELDS
helpviewer_keywords:
- PROCESS_INFO_FIELDS enumeration
ms.assetid: 0d9cc345-3d3a-44d8-ae15-a67acb97a828
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fe9a1854fe5583d001e1dc156bfad5833fd1c08f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66309461"
---
# <a name="processinfofields"></a>PROCESS_INFO_FIELDS
Указанный тип получаемых сведений для процесса.

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
 Инициализация и использование `bstrFileName` поле [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) структуры.

 `PIF_BASE_NAME`\
 Инициализация и использование `bstrBaseName` поле `PROCESS_INFO` структуры.

 `PIF_TITLE`\
 Инициализация и использование `bstrTitle` поле `PROCESS_INFO` структуры.

 `PIF_PROCESS_ID`\
 Инициализация и использование `ProcessId` поле `PROCESS_INFO` структуры.

 `PIF_SESSION_ID`\
 Инициализация и использование `dwSessionId` поле `PROCESS_INFO` структуры.

 `PIF_ATTACHED_SESSION_NAME`\
 Инициализация и использование `bstrAttachedSessionName` поле `PROCESS_INFO` структуры.

 `PIF_CREATION_TIME`\
 Инициализация и использование `CreationTime` поле `PROCESS_INFO` структуры.

 `PIF_FLAGS`\
 Инициализация и использование `Flags` поле `PROCESS_INFO` структуры.

 `PIF_ALL`\
 Заполняет все поля.

## <a name="remarks"></a>Примечания
 Передаваемый [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) метод, чтобы указать, какие поля [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) структуры должны быть инициализированы.

 Также используется в `Fields` поле `PROCESS_INFO` структура указывает, какие поля используются и допустимым.

 Эти флаги могут быть объединены с побитовым объектом `OR`.

## <a name="requirements"></a>Требования
 Header: msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)