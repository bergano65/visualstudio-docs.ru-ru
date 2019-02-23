---
title: EncUnavailableReason | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EncUnavailableReason
helpviewer_keywords:
- EncUnavailableReason enumeration
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ea1bbf8fe96abbf1e7bd9a92396d0dcfa4306445
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56717043"
---
# <a name="encunavailablereason"></a>EncUnavailableReason
`This is for internal use only!` Представляет по причинам, **изменить и продолжить** недоступна.

## <a name="syntax"></a>Синтаксис

```cpp
enum tagEncUnavailableReason {
    ENCUN_NONE,
    ENCUN_INTEROP,
    ENCUN_SQLCLR,
    ENCUN_MINIDUMP,
    ENCUN_EMBEDDED,
    ENCUN_ATTACH,
    ENCUN_WIN64
};
typedef enum tagEncUnavailableReason EncUnavailableReason;
```

```csharp
public enum EncUnavailableReason {
    ENCUN_NONE,
    ENCUN_INTEROP,
    ENCUN_SQLCLR,
    ENCUN_MINIDUMP,
    ENCUN_EMBEDDED,
    ENCUN_ATTACH,
    ENCUN_WIN64
};
```

#### <a name="parameters"></a>Параметры
ENCUN_NONE нет особых причин, почему изменить и продолжить недоступен.

ENCUN_INTEROP изменить и продолжить недоступен во время вызова взаимодействия.

ENCUN_SQLCLR изменить и продолжить недоступен во время вызова процедуры SQL, которая использует Common Language Runtime (CLR).

ENCUN_MINIDUMP изменить и продолжить недоступен во время обработки мини-дампа.

ENCUN_EMBEDDED изменить и продолжить недоступна, при обработке внедренный код.

ENCUN_ATTACH изменить и продолжить не поддерживается отладчиком, так как сеанс был подключен к, не запускается.

ENCUN_WIN64 изменить и продолжить при обработке 64-разрядный код Windows недоступна.

## <a name="remarks"></a>Примечания
Это перечисление предназначено для внутреннего использования только по [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]. [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md) и [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md) всегда должны возвращать методы как реализованный поставщика пользовательского порта `E_NOTIMPL`.

## <a name="requirements"></a>Требования
Header: msdbg.idl

Пространство имен: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)

- [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)

- [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)
