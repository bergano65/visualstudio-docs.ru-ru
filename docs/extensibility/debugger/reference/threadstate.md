---
title: С + + Документация Майкрософт
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80713338"
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
 Указывает, что поток работает.

 `THREADSTATE_STOPPED`\
 Указывает, что поток остановлен из-за точки останова.

 `THREADSTATE_FRESH`\
 Указывает, что поток был создан, но еще не выполняет код.

 `THREADSTATE_DEAD`\
 Указывает, что поток не существует.

 `THREADSTATE_FROZEN`\
 Указывает, что поток заморожен (выполнение не может быть выполнено).

## <a name="remarks"></a>Remarks
 Используется для `dwThreadState` поля структуры [среадпропертиес](../../../extensibility/debugger/reference/threadproperties.md) .

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)
