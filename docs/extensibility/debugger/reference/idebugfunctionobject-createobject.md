---
title: IDebugFunctionObject::CreateObject | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateObject
helpviewer_keywords:
- IDebugFunctionObject::CreateObject method
ms.assetid: c4c99dd5-609a-4e7c-8f29-eb728f57e995
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dc0632f429a547d4b17fe57bec4582fea623ee24
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66320948"
---
# <a name="idebugfunctionobjectcreateobject"></a>IDebugFunctionObject::CreateObject
Создает объект, с помощью конструктора.

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
[in] [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) объект, представляющий конструктор объекта должен быть создан.

`dwArgs`\
[in] Число параметров в `pArg` массива. Представляет число параметров, переданных конструктору.

`pArg`\
[in] Массив [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) объектов, представляющих параметры, переданные в конструктор.

`ppObject`\
[out] Возвращает `IDebugObject` представляющий только что созданный объект.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Вызовите этот метод, чтобы создать объект, представляющий экземпляр класса (или других сложный тип, который требуется конструктор) то есть параметра функции, который представляется [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) интерфейс.

 Если конструктор не требует параметра объекта, вызовите [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md) метод.

## <a name="see-also"></a>См. также
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
- [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)