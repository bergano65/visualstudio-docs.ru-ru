---
title: 'IDebugObject2:: "поле" | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::GetField
helpviewer_keywords:
- IDebugObject2::GetField method
ms.assetid: add6a6b5-e752-47dd-9613-29206ea809b0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 54f692fa85cfd8fa290a7f5c697a91e0366f8224
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99953465"
---
# <a name="idebugobject2getfield"></a>IDebugObject2::GetField
Возвращает тип этого объекта.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetField(
 IDebugField** ppField
);
```

```csharp
int GetField(
   out IDebugField ppField
);
```

## <a name="parameters"></a>Параметры
`ppField`\
заполняет Возвращает объект [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) , если значение не равно null.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Поле, описывающее тип объекта.

## <a name="see-also"></a>См. также раздел
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
