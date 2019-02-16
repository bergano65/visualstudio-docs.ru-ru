---
title: BP_STATE | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- BP_STATE
helpviewer_keywords:
- BP_STATE enumeration
ms.assetid: 08aa6a3f-3e5f-4c83-8eca-7b7b5f8e208d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 95e228a3aa0e96eedcf0413df7680e7a5664b707
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2019
ms.locfileid: "56315421"
---
# <a name="bpstate"></a>BP_STATE
Задает существование связанная точка останова, а также указывает, включена ли.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_BP_STATE {
    BPS_NONE     = 0x0000,
    BPS_DELETED  = 0x0001,
    BPS_DISABLED = 0x0002,
    BPS_ENABLED  = 0x0003
};
typedef DWORD BP_STATE;
```

```csharp
public enum enum_BP_STATE {
    BPS_NONE     = 0x0000,
    BPS_DELETED  = 0x0001,
    BPS_DISABLED = 0x0002,
    BPS_ENABLED  = 0x0003
};
```

## <a name="members"></a>Участники
BPS_NONE  
Указывает, что точка останова не существует.

BPS_DELETED  
Указывает, что точка останова была удалена.

BPS_DISABLED  
Указывает, что точка останова отключен.

BPS_ENABLED  
Указывает, что точка останова включена.

## <a name="remarks"></a>Примечания
Возвращаемые [GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md) метод.

## <a name="requirements"></a>Требования
Header: msdbg.h

Пространство имен: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
[Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)  
[GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)
