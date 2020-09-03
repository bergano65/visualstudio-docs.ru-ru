---
title: PENDING_BP_STATE | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PENDING_BP_STATE
helpviewer_keywords:
- PENDING_BP_STATE enumeration
ms.assetid: ac04ad72-fa92-4a15-ade2-0d0bbbadfc7f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 69c8dbe1022ee0b1b2ff034d2b83b947c8fb3df6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80713999"
---
# <a name="pending_bp_state"></a>PENDING_BP_STATE
Указывает состояние ожидающей точки останова (точка останова, которая еще не привязана).

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_PENDING_BP_STATE { 
   PBPS_NONE     = 0x0000,
   PBPS_DELETED  = 0x0001,
   PBPS_DISABLED = 0x0002,
   PBPS_ENABLED  = 0x0003
};
typedef DWORD PENDING_BP_STATE;
```

```csharp
public enum enum_PENDING_BP_STATE { 
   PBPS_NONE     = 0x0000,
   PBPS_DELETED  = 0x0001,
   PBPS_DISABLED = 0x0002,
   PBPS_ENABLED  = 0x0003
};
```

## <a name="fields"></a>Поля
 `PBPS_NONE`\
 Заполнитель для нуля. Это значение никогда не возвращается.

 `PBPS_DELETED`\
 Указывает, что ожидание точки останова было удалено.

 `PBPS_DISABLED`\
 Указывает, что ожидание точки останова отключено.

 `PBPS_ENABLED`\
 Указывает, что ожидание точки останова включено.

## <a name="remarks"></a>Remarks
 Используйте в качестве `state` члена структуры [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) .

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)
