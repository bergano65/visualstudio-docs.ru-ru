---
title: IDebugFunctionObject::CreateArrayObject (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateArrayObject
helpviewer_keywords:
- IDebugFunctionObject::CreateArrayObject method
ms.assetid: a380e53c-15f1-401f-927f-f366eea789e6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bd4c07f2b95ff3077de79d4bc63f4fad19b0c6fa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728613"
---
# <a name="idebugfunctionobjectcreatearrayobject"></a>IDebugFunctionObject::CreateArrayObject
Создает объект массива. Этот массив может содержать как примитивные, так и объектные значения экземпляра.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT CreateArrayObject( 
   OBJECT_TYPE    ot,
   IDebugField*   pClassField,
   DWORD          dwRank,
   DWORD          dwDims[],
   DWORD          dwLowBounds[],
   IDebugObject** ppObject
);
```

```csharp
int CreateArrayObject(
   enum_OBJECT_TYPE ot,
   IDebugField      pClassField,
   uint             dwRank,
   uint[]           dwDims,
   uint[]           dwLowBounds,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Параметры
`ot`\
(в) Определяет значение из [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) перечисления с указанием типа нового объекта массива.

`pClassField`\
(в) Объект [IDebugField,](../../../extensibility/debugger/reference/idebugfield.md) представляющий класс объекта, при создании массива значений экземпляра объекта. При создании массива примитивных объектов этот параметр является нулевая величина.

`dwRank`\
(в) Ранг или количество размеров массива.

`dwDims`\
(в) Размеры каждого измерения массива.

`dwLowBounds`\
(в) Происхождение каждого измерения (обычно 0 или 1).

`ppObject`\
(ваут) Возвращает объект [IDebugObject,](../../../extensibility/debugger/reference/idebugobject.md) представляющий вновь созданный массив. На самом деле это объект [IDebugArrayObject.](../../../extensibility/debugger/reference/idebugarrayobject.md)

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха, возвращается S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Вызовите этот метод для создания объекта, представляющего параметр массива для функции, представленной интерфейсом [IDebugFunction.](../../../extensibility/debugger/reference/idebugfunctionobject.md)

## <a name="see-also"></a>См. также
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
