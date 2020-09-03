---
title: ATTACH_REASON | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ATTACH_REASON
helpviewer_keywords:
- ATTACH_REASON enumeration
ms.assetid: 159fb70b-a344-4ba6-9115-b7eaa16e228f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ca871d9dac2b6f37018af925eece5c1a6f3d1585
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738123"
---
# <a name="attach_reason"></a>ATTACH_REASON
Указывает причину, по которой подсистема отладки (DE) будет присоединена к узлу программы.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_ATTACH_REASON {
    ATTACH_REASON_LAUNCH = 0x0001,
    ATTACH_REASON_USER   = 0x0002,
    ATTACH_REASON_AUTO   = 0x0003
};
typedef DWORD ATTACH_REASON;
```

```csharp
public enum enum_ATTACH_REASON {
    ATTACH_REASON_LAUNCH = 0x0001,
    ATTACH_REASON_USER   = 0x0002,
    ATTACH_REASON_AUTO   = 0x0003
};
```

## <a name="fields"></a>Поля
`ATTACH_REASON_AUTO`\
Присоединиться, так как процесс в данный момент находится в режиме отладки.

`ATTACH_REASON_LAUNCH`\
Присоединение, так как процесс был запущен.

`ATTACH_REASON_USER`\
Присоединение из-за запроса пользователя.

## <a name="remarks"></a>Remarks
Эти значения используются в качестве параметра для методов [attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) и [attach](../../../extensibility/debugger/reference/idebugprogramex2-attach.md) .

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [Attach](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)
