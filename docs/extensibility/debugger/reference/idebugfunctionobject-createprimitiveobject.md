---
title: IDebugFunctionObject::CreatePrimitiveObject Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreatePrimitiveObject
helpviewer_keywords:
- IDebugFunctionObject::CreatePrimitiveObject method
ms.assetid: 6e9dc8b6-b4e1-4abf-b6e0-e885910775bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 24b26a072a3bebda2d01a89baaf2910de96e77d1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728536"
---
# <a name="idebugfunctionobjectcreateprimitiveobject"></a>IDebugFunctionObject::CreatePrimitiveObject
Создает примитивный объект данных, такой как простой целый ряд.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT CreatePrimitiveObject( 
   OBJECT_TYPE    ot,
   IDebugObject** ppObject
);
```

```csharp
int CreatePrimitiveObject(
   enum_OBJECT_TYPE ot,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Параметры
`ot`\
(в) Значение из [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) перечисления, представляющего тип примитивного для создания.

`ppObject`\
(ваут) Возвращает [IDebugObject,](../../../extensibility/debugger/reference/idebugobject.md) представляющий вновь созданный объект.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха, возвращается S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Вызовите этот метод для создания объекта, представляющего примитивный объект, который является параметром для функции, представленной интерфейсом [IDebugFunction.](../../../extensibility/debugger/reference/idebugfunctionobject.md) Например, если строка выражения является "myString(5)", этот метод будет использоваться для создания объекта, представляющего ряд 5.

## <a name="see-also"></a>См. также
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
