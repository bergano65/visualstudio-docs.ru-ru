---
title: DISASSEMBLY_STREAM_FIELDS Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_STREAM_FIELDS
helpviewer_keywords:
- DISASSEMBLY_STREAM_FIELDS enumeration
ms.assetid: cfc9b4de-c756-4844-bea7-d9f186a51d1b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d10f2143cbefa86442e4087ac098020f5f2bd6ac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737364"
---
# <a name="disassembly_stream_fields"></a>DISASSEMBLY_STREAM_FIELDS
Определяет, какую информацию получить о поле разборки.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_DISASSEMBLY_STREAM_FIELDS {
    DSF_ADDRESS          = 0x00000001,
    DSF_ADDRESSOFFSET    = 0x00000002,
    DSF_CODEBYTES        = 0x00000004,
    DSF_OPCODE           = 0x00000008,
    DSF_OPERANDS         = 0x00000010,
    DSF_SYMBOL           = 0x00000020,
    DSF_CODELOCATIONID   = 0x00000040,
    DSF_POSITION         = 0x00000080,
    DSF_DOCUMENTURL      = 0x00000100,
    DSF_BYTEOFFSET       = 0x00000200,
    DSF_FLAGS            = 0x00000400,
    DSF_OPERANDS_SYMBOLS = 0x00010000,
    DSF_ALL              = 0x000107ff
};
typedef DWORD DISASSEMBLY_STREAM_FIELDS;
```

```csharp
public enum enum_DISASSEMBLY_STREAM_FIELDS {
    DSF_ADDRESS          = 0x00000001,
    DSF_ADDRESSOFFSET    = 0x00000002,
    DSF_CODEBYTES        = 0x00000004,
    DSF_OPCODE           = 0x00000008,
    DSF_OPERANDS         = 0x00000010,
    DSF_SYMBOL           = 0x00000020,
    DSF_CODELOCATIONID   = 0x00000040,
    DSF_POSITION         = 0x00000080,
    DSF_DOCUMENTURL      = 0x00000100,
    DSF_BYTEOFFSET       = 0x00000200,
    DSF_FLAGS            = 0x00000400,
    DSF_OPERANDS_SYMBOLS = 0x00010000,
    DSF_ALL              = 0x000107ff
};
```

## <a name="fields"></a>Поля
`DSF_ADDRESS`\
Инициализация/использование `bstrAddress` поля.

`DSF_ADDRESSOFFSET`\
Инициализация/использование `bstrAddressOffset` поля.

`DSF_CODEBYTES`\
Инициализация/использование `bstrCodeBytes` поля.

`DSF_OPCODE`\
Инициализация/использование `bstrOpCode` поля.

`DSF_OPERANDS`\
Инициализация/использование `bstrOperands` поля.

`DSF_SYMBOL`\
Инициализация/использование `bstrSymbol` поля.

`DSF_CODELOCATIONID`\
Инициализация/использование `uCodeLocationId` поля.

`DSF_POSITION`\
Инициализация/использование `posBeg` и `posEnd` поля.

`DSF_DOCUMENTURL`\
Инициализация/использование `bstrDocumentUrl` поля.

`DSF_BYTEOFFSET`\
Инициализация/использование `dwByteOffset` поля.

`DSF_FLAGS`\
Инициализация/использование `dwFlags` поля[(DISASSEMBLY_FLAGS)](../../../extensibility/debugger/reference/disassembly-flags.md).

`DSF_OPERANDS_SYMBOLS`\
Включите имена `bstrOperands` символов в поле.

`DSF_ALL`\
Определяет все поля для разборки потока.

## <a name="remarks"></a>Примечания
Прошел в качестве параметра для метода [чтения,](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) чтобы указать, какие поля структуры [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) должны быть инициализированы.

Используется для `dwFields` члена `DisassemblyData` структуры для указания того, какие поля используются и действительны при возврате структуры.

Эти значения могут быть объединены `OR`с bitwise .

## <a name="requirements"></a>Требования
Заголовок: msdbg.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
- [Прочитать](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
- [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)
