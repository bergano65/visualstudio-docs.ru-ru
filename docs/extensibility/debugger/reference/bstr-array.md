---
title: BSTR_ARRAY Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BSTR_ARRAY
helpviewer_keywords:
- BSTR_ARRAY structure
ms.assetid: 48da37f7-a237-48a9-9ff9-389c1a00862c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7e9859267cc26ec012852a1150e458c81383dfd3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737706"
---
# <a name="bstr_array"></a>BSTR_ARRAY
Структура, описывающая массив строк.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct tagBSTR_ARRAY {
    DWORD dwCount;
    BSTR* Members;
} BSTR_ARRAY;
```

```csharp
struct BSTR_ARRAY {
    DWORD    dwCount;
    string[] Members;
}
```

## <a name="members"></a>Участники
`dwCount`\
Количество строк в `Members` массиве.

`Members`\
Массив струн.

## <a name="remarks"></a>Примечания
Эта структура возвращается из метода [EnumPersistedPorts.](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)

 (только си) Каждая отдельная строка должна `Members` быть освобождена `CoTaskMemFree`с помощью, `SysFreeString`и массив должен быть освобожден с .

## <a name="requirements"></a>Требования
Заголовок: msdbg.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)
