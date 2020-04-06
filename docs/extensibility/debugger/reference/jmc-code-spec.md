---
title: JMC_CODE_SPEC Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- JMC_CODE_SPEC
helpviewer_keywords:
- JMC_CODE_SPEC structure
ms.assetid: d89498f1-4234-46d9-b4e2-abbcbca5068a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0a6746ed0df400efc7feb3fb541c57c88f78cc2c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714744"
---
# <a name="jmc_code_spec"></a>JMC_CODE_SPEC
Эта структура используется для настройки информации JustMyCode для модуля.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct _JMC_CODE_SPEC {
    BOOL fIsUserCode;
    BSTR bstrModuleName;
} JMC_CODE_SPEC;
```

```csharp
public struct JMC_CODE_SPEC {
    public int    fIsUserCode;
    public string bstrModuleName;
};
```

## <a name="members"></a>Участники
`fIsUserCode`\
Ненулевой`TRUE`( ) если модуль должен считаться кодом пользователя; в противном`FALSE`случае, ноль ( ), если модуль должен рассматриваться как внешний код и не быть отдипываться.

`bstrModuleName`\
Название модуля, о котором идет речь.

## <a name="remarks"></a>Примечания
Эта структура передается как список таких структур методу [SetJustMyCodeState.](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)

## <a name="requirements"></a>Требования
Заголовок: msdbg.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)
