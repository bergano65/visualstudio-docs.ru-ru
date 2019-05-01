---
title: IDebugFunctionObject::CreateObject | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateObject
helpviewer_keywords:
- IDebugFunctionObject::CreateObject method
ms.assetid: c4c99dd5-609a-4e7c-8f29-eb728f57e995
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 54d1e6c21cdf4e16db69cbad0947e864e7c1847e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62919414"
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

#### <a name="parameters"></a>Параметры
 `pConstructor`

 [in] [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) объект, представляющий конструктор объекта должен быть создан.

 `dwArgs`

 [in] Число параметров в `pArg` массива. Представляет число параметров, переданных конструктору.

 `pArg`

 [in] Массив [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) объектов, представляющих параметры, переданные в конструктор.

 `ppObject`

 [out] Возвращает `IDebugObject` представляющий только что созданный объект.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Вызовите этот метод, чтобы создать объект, представляющий экземпляр класса (или других сложный тип, который требуется конструктор) то есть параметра функции, который представляется [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) интерфейс.

 Если конструктор не требует параметра объекта, вызовите [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md) метод.

## <a name="see-also"></a>См. также
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
- [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)