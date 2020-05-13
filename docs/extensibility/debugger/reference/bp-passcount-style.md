---
title: BP_PASSCOUNT_STYLE Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_PASSCOUNT_STYLE
helpviewer_keywords:
- BP_PASSCOUNT_STYLE structure
ms.assetid: 0a647047-e2d5-4724-a0b8-68108425ecad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1633c5e9aa6ff251fedce83a0243664cd9e0e0a7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737914"
---
# <a name="bp_passcount_style"></a>BP_PASSCOUNT_STYLE
Определяет условие, связанное с количеством проходов точки разрыва, что приводит к возгоранию точки разрыва.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_BP_PASSCOUNT_STYLE {
    BP_PASSCOUNT_NONE             = 0x0000,
    BP_PASSCOUNT_EQUAL            = 0x0001,
    BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,
    BP_PASSCOUNT_MOD              = 0x0003
};
typedef DWORD BP_PASSCOUNT_STYLE;
```

```csharp
public enum enum_BP_PASSCOUNT_STYLE {
    BP_PASSCOUNT_NONE             = 0x0000,
    BP_PASSCOUNT_EQUAL            = 0x0001,
    BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,
    BP_PASSCOUNT_MOD              = 0x0003
};
```

## <a name="fields"></a>Поля
`BP_PASSCOUNT_NONE`\
Указывает не тип подсчета очков брейк-пойнта.

`BP_PASSCOUNT_EQUAL`\
Устанавливает стиль подсчета проходов брейк-пойнта на равный. Точка разрыва сражается, когда количество ударов по точке разрыва равно количеству проходов.

`BP_PASSCOUNT_EQUAL_OR_GREATER`\
Устанавливает стиль подсчета проходов точки разрыва на равный или больше. Точка разрыва сражается, когда количество ударов по точке разрыва равно или больше, чем количество проходов.

`BP_PASSCOUNT_MOD`\
Определяет количество пропусков модуло. Например, если количество проходов `BP_PASSCOUNT_MOD` имеет тип, а значение количества проходов составляет 4, точка разрыва сражается каждый раз, когда количество попаданий кратно ежей 4.

## <a name="remarks"></a>Примечания
Используется для `stylePassCount` члена [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) структуры, которая, в свою очередь, является членом [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) и [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) структур.

## <a name="requirements"></a>Требования
Заголовок: msdbg.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
