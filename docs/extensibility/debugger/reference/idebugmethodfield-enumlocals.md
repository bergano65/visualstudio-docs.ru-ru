---
title: IDebugMethodfield::EnumLocals Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumLocals
helpviewer_keywords:
- IDebugMethodField::EnumLocals method
ms.assetid: b0456a6d-2b96-49e2-a871-516571b4f6a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 08872160860d0d442f9807705dea70190dff9b28
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727202"
---
# <a name="idebugmethodfieldenumlocals"></a>IDebugMethodField::EnumLocals
Создает регистратор для отдельных локальных переменных метода.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT EnumLocals(
    IDebugAddress*     pAddress,
    IEnumDebugFields** ppLocals
);
```

```csharp
int EnumLocals(
    IDebugAddress        pAddress,
    out IEnumDebugFields ppLocals
);
```

## <a name="parameters"></a>Параметры
`pAddress`\
(в) Объект [IDebugAddress,](../../../extensibility/debugger/reference/idebugaddress.md) представляющий адрес отладки, который выбирает контекст или область, из которой можно получить местных жителей.

`ppLocals`\
(ваут) Возвращает объект [IEnumDebugFields,](../../../extensibility/debugger/reference/ienumdebugfields.md) представляющий список местных жителей; в противном случае, возвращает нулевую стоимость, если Нет местных жителей.

## <a name="return-value"></a>Возвращаемое значение
В случае успеха, возвращается S_OK или возвращается S_FALSE, если Нет местных жителей. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Примечания
Перечисляются только переменные, определяемые в блоке, содержащем данный адрес отладки. Если все местные жители, включая местных жителей, генерируемых компиляторами, необходимы, позвоните в метод [EnumAllLocals.](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)

Метод может содержать несколько контекстов или блоков. Например, следующий надуманный метод содержит три области: два внутренних блока и сам корпус метода.

```csharp
public void func(int index)
{
    // Method body scope
    int a = 0;
    if (index == 1)
    {
        // Inner scope 1
        int temp1 = a;
    }
    else
    {
        // Inner scope 2
        int temp2 = a;
    }
}
```

Объект [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) представляет `func` сам метод. Вызов `EnumLocals` метода с [iDebugАдрес,](../../../extensibility/debugger/reference/idebugaddress.md) установленный на `Inner Scope 1` адрес, `temp1` возвращает, например, перечисление, содержащее переменную.

## <a name="see-also"></a>См. также
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)
