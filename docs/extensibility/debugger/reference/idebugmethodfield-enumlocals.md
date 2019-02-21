---
title: IDebugMethodField::EnumLocals | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugMethodField::EnumLocals
helpviewer_keywords:
- IDebugMethodField::EnumLocals method
ms.assetid: b0456a6d-2b96-49e2-a871-516571b4f6a5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ba6cd5e65c54355ec21d22d101d94270b95018e8
ms.sourcegitcommit: 845442e2b515c3ca1e4e47b46cc1cef4df4f08d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/20/2019
ms.locfileid: "56450416"
---
# <a name="idebugmethodfieldenumlocals"></a>IDebugMethodField::EnumLocals
Создает перечислитель для выбранного локальные переменные метода.

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

#### <a name="parameters"></a>Параметры
`pAddress`  
[in] [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) объект, представляющий адрес отладки, который выбирает контекст или область, из которого необходимо получить "Локальные".

`ppLocals`  
[out] Возвращает [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) объект, представляющий список "Локальные"; в противном случае возвращает значение null, если нет локальных переменных.

## <a name="return-value"></a>Возвращаемое значение
В случае успешного выполнения возвращает значение S_OK, или возвращает значение S_FALSE, если нет локальных переменных. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Примечания
Перечисляются только те переменные, определенные внутри блока, который содержит адрес заданной отладочной. Если необходимы все локальные переменные, включая любые локальные переменные, создаваемые компилятором, вызвать [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md) метод.

Метод может содержать несколько контекстов или блоки области. Например следующий метод надуманный содержит три области действия, внутреннее двух блоков и самом теле метода.

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

[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) представляет объект `func` сам метод. Вызов `EnumLocals` метод с [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) присвоено `Inner Scope 1` адрес возвращает перечисление, содержащее `temp1` переменной, например.

## <a name="see-also"></a>См. также
[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)  
[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)  
[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)  
[EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)
