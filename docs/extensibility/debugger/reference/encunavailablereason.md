---
title: EncUnavailableReason | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EncUnavailableReason
helpviewer_keywords:
- EncUnavailableReason enumeration
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7db94a181d87791edb242d69b461f90c42a5e080
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318160"
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

## <a name="fields"></a>Поля
`ENCUN_NONE`\
Нет особых причин, почему изменить и продолжить недоступен.

`ENCUN_INTEROP`\
Изменить и продолжить недоступен во время вызова взаимодействия.

`ENCUN_SQLCLR`\
Изменить и продолжить недоступен во время вызова процедуры SQL, которая использует Common Language Runtime (CLR).

`ENCUN_MINIDUMP`\
Изменить и продолжить недоступен во время обработки мини-дампа.

`ENCUN_EMBEDDED`\
Изменить и продолжить недоступна, при обработке внедренный код.

`ENCUN_ATTACH`\
Изменить и продолжить недоступно, так как сеанс был подключен к, не запускается отладчиком,.

`ENCUN_WIN64`\
Изменить и продолжить при обработке 64-разрядный код Windows недоступна.

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
