---
title: CANSTOP_REASON | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CANSTOP_REASON
helpviewer_keywords:
- CANSTOP_REASON enumeration
ms.assetid: 6da944eb-36cd-4a8c-8d71-544c775cfcc1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 18861d7aa19281528e9a100f57399451194598a9
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66327254"
---
# <a name="canstopreason"></a>CANSTOP_REASON
Используется для определения того, если программы можно остановить выполнение после достижения определенной точке выполнения.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_CANSTOP_REASON {
    CANSTOP_ENTRYPOINT = 0x0000,
    CANSTOP_STEPIN     = 0x0001
};
typedef DWORD CANSTOP_REASON;
```

```csharp
public enum enum_CANSTOP_REASON {
    CANSTOP_ENTRYPOINT = 0x0000,
    CANSTOP_STEPIN     = 0x0001
};
```

## <a name="fields"></a>Поля
`CANSTOP_ENTRYPOINT`\
Определяет точку входа данной программы.

`CANSTOP_STEPIN`\
Указывает, шаг с заходом в функцию.

## <a name="remarks"></a>Примечания
Передается в качестве аргумента для [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) метод подтверждения с сеанса отладки Manager (SDM), если необходимо остановить после достижения точки входа программы или шаг с заходом в функции или метода.

## <a name="requirements"></a>Требования
Header: msdbg.h

Пространство имен: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
