---
title: BP_LOCATION_TYPE Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_TYPE
helpviewer_keywords:
- BP_LOCATION_TYPE structure
ms.assetid: 0248430a-3b61-4809-87a9-e9b6bb7d1130
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 50e6bdc0dba8f6bcbdd55c45132dff02735786d6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737944"
---
# <a name="bp_location_type"></a>BP_LOCATION_TYPE
Определяет тип местоположения точки разрыва для запроса точки разрыва.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_BP_LOCATION_TYPE {
    BPLT_NONE               = 0x00000000,
    BPLT_FILE_LINE          = 0x00010000,
    BPLT_FUNC_OFFSET        = 0x00020000,
    BPLT_CONTEXT            = 0x00030000,
    BPLT_STRING             = 0x00040000,
    BPLT_ADDRESS            = 0x00050000,
    BPLT_RESOLUTION         = 0x00060000,
    BPLT_CODE_FILE_LINE     = BPT_CODE | BPLT_FILE_LINE,
    BPLT_CODE_FUNC_OFFSET   = BPT_CODE | BPLT_FUNC_OFFSET,
    BPLT_CODE_CONTEXT       = BPT_CODE | BPLT_CONTEXT,
    BPLT_CODE_STRING        = BPT_CODE | BPLT_STRING,
    BPLT_CODE_ADDRESS       = BPT_CODE | BPLT_ADDRESS ,
    BPLT_DATA_STRING        = BPT_DATA | BPLT_STRING,
    BPLT_TYPE_MASK          = 0x0000FFFF,
    BPLT_LOCATION_TYPE_MASK = 0xFFFF0000
};
typedef DWORD BP_LOCATION_TYPE;
```

```csharp
public enum enum_BP_LOCATION_TYPE {
    BPLT_NONE               = 0x00000000,
    BPLT_FILE_LINE          = 0x00010000,
    BPLT_FUNC_OFFSET        = 0x00020000,
    BPLT_CONTEXT            = 0x00030000,
    BPLT_STRING             = 0x00040000,
    BPLT_ADDRESS            = 0x00050000,
    BPLT_RESOLUTION         = 0x00060000,
    BPLT_CODE_FILE_LINE     = BPT_CODE | BPLT_FILE_LINE,
    BPLT_CODE_FUNC_OFFSET   = BPT_CODE | BPLT_FUNC_OFFSET,
    BPLT_CODE_CONTEXT       = BPT_CODE | BPLT_CONTEXT,
    BPLT_CODE_STRING        = BPT_CODE | BPLT_STRING,
    BPLT_CODE_ADDRESS       = BPT_CODE | BPLT_ADDRESS ,
    BPLT_DATA_STRING        = BPT_DATA | BPLT_STRING,
    BPLT_TYPE_MASK          = 0x0000FFFF,
    BPLT_LOCATION_TYPE_MASK = 0xFFFF0000
};
```

## <a name="fields"></a>Поля
`BPLT_NONE`\
Указывает отсутствие местоположения точки разрыва.

`BPLT_FILE_LINE`\
Определяет тип местоположения точки разрыва в виде строки файла.

`BPLT_FUNC_OFFSET`\
Определяет тип местоположения точки разрыва в качестве смещения функции.

`BPLT_CONTEXT`\
Определяет тип местоположения точки разрыва в виде контекста.

`BPLT_STRING`\
Определяет тип местоположения точки разрыва в виде строки.

`BPLT_ADDRESS`\
Укажите тип определения типа точки разрыва в качестве адреса.

`BPLT_RESOLUTION`\
Определяет тип местоположения точки разрыва в виде разрешения.

`BPLT_CODE_FILE_LINE`\
Определяет тип местоположения точки разрыва в виде строки исходного кода.

`BPLT_CODE_FUNC_OFFSET`\
Определяет тип местоположения точки разрыва в качестве смещения функции кода.

`BPLT_CODE_CONTEXT`\
Определяет тип местоположения точки разрыва в виде контекста кода.

`BPLT_CODE_STRING`\
Определяет тип местоположения точки разрыва в строке кода.

`BPLT_CODE_ADDRESS`\
Укажите тип определения типа точки разрыва в качестве кода.

`BPLT_DATA_STRING`\
Определяет тип определения типа точки разрыва в виде строки данных.

`BPLT_TYPE_MASK`\
Укажите немного маски, так что тип точки разрыва может быть извлечен из значения.

`BPLT_LOCATION_TYPE_MASK`\
Укажите немного маски, так что тип местоположения брейка может быть извлечен из значения.

## <a name="remarks"></a>Примечания
Прошел в качестве параметра к методу [GetLocationType.](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)

Тип точки разрыва состоит из типа точки разрыва и типа местоположения. Это означает, что тип точки разрыва никогда не является `BPT_CODE`просто типом точки разрыва `BPLT_FILE_LINE`(например, ) или типом местоположения (например, ). Предопределенные константы для всех типов определения местоположения брейк-пойнтов, поддерживаемых в настоящее время, включены в этот пересчет (через).`BPLT_CODE_FILE_LINE` `BPLT_DATA_STRING`

`BPT_CODE`и `BPT_DATA` являются членами [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) перечисления.

## <a name="requirements"></a>Требования
Заголовок: msdbg.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)
- [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)
