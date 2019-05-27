---
title: IDebugObject::GetValue | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetValue
helpviewer_keywords:
- IDebugObject::GetValue method
ms.assetid: eec6051e-8ecb-49fa-bdd4-dd786f211692
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4e6fd1d3b4d7effe0f4c6f5f0434a01422345f00
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66202884"
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