---
title: DISASSEMBLY_FLAGS Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_FLAGS
helpviewer_keywords:
- DISASSEMBLY_FLAGS enumeration
ms.assetid: c1ec5a4d-5d42-4660-932c-7348550140cb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ba6d9db3ad2cb1f9bbc9e3cea27aba939c6dd499
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737370"
---
# <a name="disassembly_flags"></a>DISASSEMBLY_FLAGS
Определяет флаги для разборки.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_DISASSEMBLY_FLAGS {
    DF_DOCUMENTCHANGE     = 0x00000001,
    DF_DISABLED           = 0x00000002,
    DF_INSTRUCTION_ACTIVE = 0x00000004,
    DF_DATA               = 0x00000008,
    DF_HASSOURCE          = 0x00000010,
    DF_DOCUMENT_CHECKSUM  = 0x00000020
};
typedef DWORD DISASSEMBLY_FLAGS;
```

```csharp
public enum enum_DISASSEMBLY_FLAGS {
    DF_DOCUMENTCHANGE     = 0x00000001,
    DF_DISABLED           = 0x00000002,
    DF_INSTRUCTION_ACTIVE = 0x00000004,
    DF_DATA               = 0x00000008,
    DF_HASSOURCE          = 0x00000010,
    DF_DOCUMENT_CHECKSUM  = 0x00000020
};
```

## <a name="fields"></a>Поля
`DF_DOCUMENTCHANGE`\
Указывается, что эта инструкция содержится в другом документе, чем предыдущая.

`DF_DISABLED`\
Означает, что эта инструкция не будет выполнена.

`DF_INSTRUCTION_ACTIVE`\
Указывает, что эта инструкция является одним из следующих инструкций, которые должны быть выполнены (может быть более одного).

`DF_DATA`\
Означает, что эта инструкция на самом деле данные (не код).

`DF_HASSOURCE`\
Означает, что эта инструкция имеет источник. Некоторые инструкции, такие как код профилирования или сбора мусора, не имеют соответствующего источника.

`DF_DOCUMENT_CHECKSUM`\
Указывает, `bstrDocumentUrl` что поле содержит данные проверки после URL документа. О том, как хранятся данные checksum, можно ознакомиться в разделе «Замечания» для структуры [DisassemblyData.](../../../extensibility/debugger/reference/disassemblydata.md)

## <a name="remarks"></a>Примечания
Используется в `dwFlags` качестве члена структуры [DisassemblyData.](../../../extensibility/debugger/reference/disassemblydata.md)

Эти флаги могут быть `OR`объединены с bitwise .

## <a name="requirements"></a>Требования
Заголовок: msdbg.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
