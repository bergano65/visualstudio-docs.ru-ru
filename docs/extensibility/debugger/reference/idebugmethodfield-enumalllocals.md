---
title: IDebugMethodfield::EnumAllLocals Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumAllLocals
helpviewer_keywords:
- IDebugMethodField::EnumAllLocals method
ms.assetid: 0bc7cc13-2628-4bd8-8c06-4d2aa6755ea8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 50da5af616c56276a0299a0d08e6eeb0b88181cc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727343"
---
# <a name="idebugmethodfieldenumalllocals"></a>IDebugMethodField::EnumAllLocals
Создает список для всех локальных переменных метода, включая те, которые генерируются внутри компилятора.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT EnumAllLocals( 
   IDebugAddress*     pAddress,
   IEnumDebugFields** ppLocals
);
```

```csharp
int EnumAllLocals(
   IDebugAddress        pAddress,
   out IEnumDebugFields ppLocals
);
```

## <a name="parameters"></a>Параметры
`pAddress`\
(в) Объект [IDebugAddress,](../../../extensibility/debugger/reference/idebugaddress.md) представляющий адрес отладки в методе, указывающий на определенный объем или контекст.

`ppLocals`\
(ваут) Возвращает объект [IEnumDebugFields,](../../../extensibility/debugger/reference/ienumdebugfields.md) представляющий список всех местных жителей в указанной области; в противном случае, возвращает нулевую стоимость, указывающую на отсутствие местных жителей.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха, возвращается S_OK или возвращается S_FALSE, если Нет местных жителей. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Примечания
 Перечисляются только переменные, определяемые в блоке, содержащем данный адрес отладки. Этот метод включает в себя все местные жители, генерируемые компилятором. Если все, что необходимо, это местные жители, четко определенные в источнике, позвоните в метод [EnumLocals.](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)

 Метод может содержать несколько контекстов или блоков.

## <a name="see-also"></a>См. также
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)
