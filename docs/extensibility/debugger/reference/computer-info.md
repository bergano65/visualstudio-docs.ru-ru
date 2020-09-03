---
title: COMPUTER_INFO | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- COMPUTER_INFO structure
ms.assetid: 943085b2-f165-462d-9a4e-2086f0cdfff4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 27794dff51646b72dbbfda81ead02e5206ade78b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737655"
---
# <a name="computer_info"></a>COMPUTER_INFO
Описывает компьютер, на котором работает отладчик.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct tagCOMPUTER_INFO
{
    WORD wProcessorArchitecture;
    WORD wSuiteMask;
    DWORD dwOperatingSystemVersion;
} COMPUTER_INFO;
```

```csharp
public struct COMPUTER_INFO
{
    public ushort wProcessorArchitecture;
    public ushort wSuiteMask;
    public uint dwOperatingSystemVersion;
}
```

## <a name="members"></a>Участники
`wProcessorArchitecture`\
Определяет архитектуру микропроцессора.

`wSuiteMask`\
Определяет маску набора.

`dwOperatingSystemVersion`\
Номер версии операционной системы.

## <a name="remarks"></a>Remarks
Эта структура возвращается методом [жеткомпутеринфо](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md) .

## <a name="requirements"></a>Требования
Заголовок: Мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [жеткомпутеринфо](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)
