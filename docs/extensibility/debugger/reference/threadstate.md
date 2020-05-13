---
title: НИТИ-ГОСУДАРСТВО Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADSTATE
helpviewer_keywords:
- THREADSTATE enumeration
ms.assetid: 62efdd7c-25b1-4fd3-9d06-ac1830a418a9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1b291cc1668b2b867729da11d4c561f74567f257
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713338"
---
# <a name="threadstate"></a>THREADSTATE
Определяет состояние потока.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_THREADSTATE { 
   THREADSTATE_RUNNING = 0x0001,
   THREADSTATE_STOPPED = 0x0002,
   THREADSTATE_FRESH   = 0x0003,
   THREADSTATE_DEAD    = 0x0004,
   THREADSTATE_FROZEN  = 0x0005
};
typedef DWORD THREADSTATE;
```

```csharp
public enum enum_THREADSTATE { 
   THREADSTATE_RUNNING = 0x0001,
   THREADSTATE_STOPPED = 0x0002,
   THREADSTATE_FRESH   = 0x0003,
   THREADSTATE_DEAD    = 0x0004,
   THREADSTATE_FROZEN  = 0x0005
};
```

## <a name="fields"></a>Поля
 `THREADSTATE_RUNNING`\
 Означает, что поток работает.

 `THREADSTATE_STOPPED`\
 Означает, что поток остановлен из-за точки разрыва.

 `THREADSTATE_FRESH`\
 Означает, что поток создан, но еще не запущен код.

 `THREADSTATE_DEAD`\
 Означает, что поток мертв.

 `THREADSTATE_FROZEN`\
 Означает, что поток заморожен (выполнение не может быть выполнено).

## <a name="remarks"></a>Примечания
 Используется для `dwThreadState` поля структуры [THREADPROPERTIES.](../../../extensibility/debugger/reference/threadproperties.md)

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)
