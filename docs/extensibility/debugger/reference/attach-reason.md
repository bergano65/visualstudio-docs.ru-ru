---
title: ATTACH_REASON Документы Майкрософт
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738123"
---
# <a name="attach_reason"></a>ATTACH_REASON
Определяет причину присоединения двигателя отладки (DE) к узлову программы.

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
Прикрепите, потому что процесс в настоящее время находится в режиме отладки.

`ATTACH_REASON_LAUNCH`\
Прикрепите, потому что процесс запущен.

`ATTACH_REASON_USER`\
Прикрепите из-за запроса пользователя.

## <a name="remarks"></a>Примечания
Эти значения используются в качестве параметра для методов [присоединения](../../../extensibility/debugger/reference/idebugengine2-attach.md) и [присоединения.](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)

## <a name="requirements"></a>Требования
Заголовок: msdbg.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [Attach](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)
