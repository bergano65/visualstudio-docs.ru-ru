---
title: BSTR_ARRAY | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BSTR_ARRAY
helpviewer_keywords:
- BSTR_ARRAY structure
ms.assetid: 48da37f7-a237-48a9-9ff9-389c1a00862c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 24222b60db1ba35da59069e58d6f1377928e7a54
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56714924"
---
# <a name="bstrarray"></a>BSTR_ARRAY
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

## <a name="terms"></a>Термины
dwCount несколько строк в `Members` массива.

Элементы массива строк.

## <a name="remarks"></a>Примечания
Эта структура возвращается из [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md) метод.


 [C++] Каждой отдельной строки должны быть высвобождены с помощью `SysFreeString`и `Members` массива должны быть высвобождены с `CoTaskMemFree`.

## <a name="requirements"></a>Требования
Header: msdbg.h

Пространство имен: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)
