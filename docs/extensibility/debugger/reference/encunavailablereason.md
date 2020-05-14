---
title: EncUnavailableПричина (англ.) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EncUnavailableReason
helpviewer_keywords:
- EncUnavailableReason enumeration
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 28863549ab3eac96322530bc85c52697f20448c8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737168"
---
# <a name="encunavailablereason"></a>EncUnavailableReason
`This is for internal use only!`Представляет причины, по которым **edit and Continue** недоступен.

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
Нет конкретной причины, почему Edit and Continue не доступна.

`ENCUN_INTEROP`\
Edit and Continue недоступен во время вызова InterOp.

`ENCUN_SQLCLR`\
Исправление и продолжение недоступно во время процедуры S'L, в котором используется общее время выполнения языка (CLR).

`ENCUN_MINIDUMP`\
Edit and Continue недоступен при обработке мини-дампа.

`ENCUN_EMBEDDED`\
Edit and Continue недоступен при обработке встроенного кода.

`ENCUN_ATTACH`\
Edit and Continue недоступен, поскольку сеанс был прикреплен к отладчику, а не запущенному.

`ENCUN_WIN64`\
Edit and Continue недоступен при обработке 64-битного кода Windows.

## <a name="remarks"></a>Примечания
Это перечисление предназначено для [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]внутреннего использования только . Методы [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md) и [DisableENC,](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md) реализованные поставщиком `E_NOTIMPL`портов, должны всегда возвращаться.

## <a name="requirements"></a>Требования
Заголовок: msdbg.idl

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)

- [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)

- [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)
