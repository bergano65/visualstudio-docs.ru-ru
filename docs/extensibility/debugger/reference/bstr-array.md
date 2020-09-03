---
title: BSTR_ARRAY | Документация Майкрософт
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
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
Массив строк.

## <a name="remarks"></a>Remarks
Эта структура возвращается методом [енумперсистедпортс](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md) .

 [Только C++] Каждая отдельная строка должна быть освобождена с помощью `SysFreeString` , а `Members` массив должен быть освобожден с использованием `CoTaskMemFree` .

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)
