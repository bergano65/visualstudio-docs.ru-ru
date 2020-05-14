---
title: IDebugFunctionObject::CreateObject Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateObject
helpviewer_keywords:
- IDebugFunctionObject::CreateObject method
ms.assetid: c4c99dd5-609a-4e7c-8f29-eb728f57e995
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: beb00bcf932b19ed4e489456236957c55d909ce4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728593"
---
# <a name="idebugfunctionobjectcreateobject"></a>IDebugFunctionObject::CreateObject
Создает объект с помощью конструктора.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT CreateObject( 
   IDebugFunctionObject* pConstructor,
   DWORD                 dwArgs,
   IDebugObject*         pArgs[],
   IDebugObject**        ppObject
);
```

```csharp
int CreateObject(
   IDebugFunctionObject pConstructor,
   uint                 dwArgs,
   IDebugObject[]       pArgs,
   out IDebugObject     ppObject
);
```

## <a name="parameters"></a>Параметры
`pConstructor`\
(в) Объект [IDebugFunctionObject,](../../../extensibility/debugger/reference/idebugfunctionobject.md) представляющий конструктор амортизации, который должен быть создан.

`dwArgs`\
(в) Количество параметров в `pArg` массиве. Представляет количество параметров, переданных конструктору.

`pArg`\
(в) Массив объектов [IDebugObject,](../../../extensibility/debugger/reference/idebugobject.md) представляющих параметры, передаваемые конструктору.

`ppObject`\
(ваут) Возвращает `IDebugObject` представляющий вновь созданный объект.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха, возвращается S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Вызовите этот метод для создания объекта, представляющего экземпляр класса (или другого сложного типа, требующего конструктора), который является параметром функции, представленной интерфейсом [IDebugFunctionObject.](../../../extensibility/debugger/reference/idebugfunctionobject.md)

 Если параметр объекта не требует конструктора, позвоните в метод [CreateObjectNoConstructor.](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)

## <a name="see-also"></a>См. также
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
- [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)
