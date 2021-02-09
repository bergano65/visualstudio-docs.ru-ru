---
title: 'Идебугобжект:: GetValue | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetValue
helpviewer_keywords:
- IDebugObject::GetValue method
ms.assetid: eec6051e-8ecb-49fa-bdd4-dd786f211692
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f7534a05879bdae0a885ae0cbe23d072c30132d0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99846807"
---
# <a name="idebugobjectgetvalue"></a>IDebugObject::GetValue
Возвращает значение объекта в виде последовательности байтов.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetValue( 
   BYTE* pValue,
   UINT  nSize
);
```

```csharp
int GetValue(
   ref byte[] pValue,
   uint nSize
);
```

## <a name="parameters"></a>Параметры
`pValue`\
[вход, выход] Массив, который заполняется последовательными последовательностями байтов, представляющими значение объекта.

`nSize`\
окне Максимальное число извлекаемых байтов.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Возвращает общее количество байтов значений, которые можно получить, вызвав [метод GetBytes](../../../extensibility/debugger/reference/idebugobject-getsize.md) .

## <a name="see-also"></a>См. также раздел
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
