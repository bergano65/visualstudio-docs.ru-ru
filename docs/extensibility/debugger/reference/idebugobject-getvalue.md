---
title: IDebugObject::GetValue | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetValue
helpviewer_keywords:
- IDebugObject::GetValue method
ms.assetid: eec6051e-8ecb-49fa-bdd4-dd786f211692
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 59d58e136045bb4177755c981f91974f9ac2fa77
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66323652"
---
# <a name="idebugobjectgetvalue"></a>IDebugObject::GetValue
Возвращает значение объекта как ряд последовательных байтов.

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
[in, out] Массив, который заполняется последовательных последовательность байтов, представляющий значение объекта.

`nSize`\
[in] Максимальное число байтов для получения.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Получить общее значение байтов, которые могут быть извлечены, вызвав [GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md) метод.

## <a name="see-also"></a>См. также
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)