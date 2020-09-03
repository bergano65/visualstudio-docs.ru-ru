---
title: 'Идебугмесодфиелд:: Енумалллокалс | Документация Майкрософт'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80727343"
---
# <a name="idebugmethodfieldenumalllocals"></a>IDebugMethodField::EnumAllLocals
Создает перечислитель для всех локальных переменных метода, включая созданные внутри компилятора.

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
окне Объект [идебугаддресс](../../../extensibility/debugger/reference/idebugaddress.md) , представляющий адрес отладки в методе, указывающий на конкретную область или контекст.

`ppLocals`\
заполняет Возвращает объект [иенумдебугфиелдс](../../../extensibility/debugger/reference/ienumdebugfields.md) , представляющий список всех локальных переменных в указанной области. в противном случае возвращает значение null, указывающее, что локальные переменные отсутствуют.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK или возвращает S_FALSE, если нет локальных переменных. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Remarks
 Перечисляются только те переменные, которые определены в блоке, содержащем заданный адрес отладки. Этот метод включает все созданные компилятором локальные переменные. Если все, что требуется, — это локальные переменные, явно определенные в источнике, вызовите метод [енумлокалс](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) .

 Метод может содержать несколько контекстов области или блоков.

## <a name="see-also"></a>См. также раздел
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)
