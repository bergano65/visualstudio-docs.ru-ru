---
title: 'Идебугаддресс:: @ Address | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress::GetAddress
helpviewer_keywords:
- IDebugAddress:GetAddress method
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: df4eb1278a0fe436899c1da989c4c63cfa98cac3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99853016"
---
# <a name="idebugaddressgetaddress"></a>IDebugAddress::GetAddress
Возвращает структуру, описывающую объект и его расположение в области или контейнере.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetAddress (
   DEBUG_ADDRESS * pAddress
);
```

```csharp
int GetAddress(
   DEBUG_ADDRESS[] pAddress
);
```

## <a name="parameters"></a>Параметры
`pAddress`\
[вход, выход] Структура [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) , которая заполняется этим методом.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Структура [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) передается в этот метод, который затем заполняет его соответствующими данными. Способ интерпретации этой информации зависит от типа возвращаемой информации и самого обработчика символов. Дополнительные сведения см. в разделе [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) .

## <a name="see-also"></a>См. также раздел
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
