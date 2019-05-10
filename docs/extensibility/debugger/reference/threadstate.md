---
title: THREADSTATE | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADSTATE
helpviewer_keywords:
- THREADSTATE enumeration
ms.assetid: 62efdd7c-25b1-4fd3-9d06-ac1830a418a9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3019671b98d3eb17c92d97c368f2f7338ee55a1d
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/09/2019
ms.locfileid: "65460714"
---
# <a name="threadstate"></a>THREADSTATE
Указывает состояние потока.

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
 Указывает, что поток выполняется.

 `THREADSTATE_STOPPED`\
 Указывает, что поток остановлен из-за точки останова.

 `THREADSTATE_FRESH`\
 Указывает, что поток будет создана, но еще не выполняется код.

 `THREADSTATE_DEAD`\
 Указывает, что поток бездействует.

 `THREADSTATE_FROZEN`\
 Указывает, что поток заморожен (выполнение не может выполняться).

## <a name="remarks"></a>Примечания
 Используется для `dwThreadState` поле [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) структуры.

## <a name="requirements"></a>Требования
 Header: msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)