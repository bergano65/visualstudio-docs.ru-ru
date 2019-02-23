---
title: IDebugPointerObject3::GetPointerAddress | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetPointerAddress
- IDebugPointerObject3::GetPointerAddress
ms.assetid: 4cc5af04-9e70-420d-8230-ef3108df6d51
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1066453c502d7935e43f1af467431f9b9a8f80b8
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56706825"
---
# <a name="idebugpointerobject3getpointeraddress"></a>IDebugPointerObject3::GetPointerAddress
Извлекает адрес указателя.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetPointerAddress (
   UINT64* puAddress
);
```

```csharp
int GetPointerAddress (
   out ulong puAddress
);
```

#### <a name="parameters"></a>Параметры
 `puAddress`

 [out] Возвращает адрес указателя.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)