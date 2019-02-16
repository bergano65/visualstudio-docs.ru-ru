---
title: COMPUTER_INFO | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- COMPUTER_INFO structure
ms.assetid: 943085b2-f165-462d-9a4e-2086f0cdfff4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 183c079206dd4c16a9301e370abec2f9351b1f61
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2019
ms.locfileid: "56316838"
---
# <a name="computerinfo"></a>COMPUTER_INFO
Описание компьютера, на котором выполняется отладчик.

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

## <a name="terms"></a>Термины
wProcessorArchitecture  
Указывает архитектуру процессора.

wSuiteMask  
Определяет набор маски.

dwOperatingSystemVersion  
Номер версии операционной системы.

## <a name="remarks"></a>Примечания
Эта структура возвращается [GetComputerInfo](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md) метод.

## <a name="requirements"></a>Требования
Заголовок: Msdbg.h

Пространство имен: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
[Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)  
[GetComputerInfo](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)
