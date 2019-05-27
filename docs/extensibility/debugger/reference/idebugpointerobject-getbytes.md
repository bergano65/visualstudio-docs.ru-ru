---
title: IDebugPointerObject::GetBytes | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::GetBytes
helpviewer_keywords:
- IDebugPointerObject::GetBytes method
ms.assetid: e986c188-87fb-4b51-86e9-ee6a0035bdab
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d108613c7a557c189a2c42880a5618b42e0bd3b8
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66209388"
---
# <a name="idebugpointerobjectgetbytes"></a>IDebugPointerObject::GetBytes
Получает значение, на которую указывает как ряд последовательных байтах.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetBytes( 
   DWORD  dwStart,
   DWORD  dwCount,
   BYTE*  pBytes,
   DWORD* pdwBytes
);
```

```csharp
int GetBytes(
   uint       dwStart,
   uint       dwCount,
   out byte[] pBytes,
   out uint   pdwBytes
);
```

## <a name="parameters"></a>Параметры
`dwStart`\
[in] Указывает смещение в байтах от начала объекта.

`dwCount`\
[in] Число байтов для получения.

`pBytes`\
[in, out] Массив, который заполняется значение как ряд последовательных байтах, начиная с заданного смещения из объекта, на которые указывают.

`pdwBytes`\
[out] Возвращает число фактически извлеченных байтов.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Этот метод используется в том случае, если указатель, представленного этим объектом [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) указывает на тип-примитив или простого массива типов-примитивов (то есть массив, могут быть представлены простые последовательности байтов).

## <a name="see-also"></a>См. также
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
- [SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)