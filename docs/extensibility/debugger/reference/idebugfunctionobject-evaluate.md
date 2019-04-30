---
title: IDebugFunctionObject::Evaluate | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::Evaluate
helpviewer_keywords:
- IDebugFunctionObject::Evaluate method
ms.assetid: 29349ea3-d5c1-4135-aa76-ced073ab9683
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9deaf32a88d476895feab006cbe3b818d11b97ca
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62873949"
---
# <a name="idebugfunctionobjectevaluate"></a>IDebugFunctionObject::Evaluate
Вызывает функцию и возвращает результирующее значение как объект.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Evaluate( 
   IDebugObject** ppParams,
   DWORD          dwParams,
   DWORD          dwTimeout,
   IDebugObject** ppResult
);
```

```csharp
int Evaluate(
   IDebugObject[]   ppParams,
   IntPtr           dwParams,
   uint             dwTimeout,
   out IDebugObject ppResult
);
```

#### <a name="parameters"></a>Параметры
 `ppParams`

 [in] Массив [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) объекты, представляющие входные параметры. Каждый из этих параметров был создан с помощью одного из `Create` методы в [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) интерфейс.

 `dwParams`

 [in] Число параметров в `ppParams` массива.

 `dwTimeout`

 [in] Указывает максимальное время в миллисекундах для ожидания перед возвратом из этого метода. Используйте `INFINITE` для неограниченного времени ожидания.

 `ppResult`

 [out] Возвращает [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) представляющая значение функции в виде объекта.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Этот метод настраивает и выполняет вызов функции, представленной [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) объекта.

## <a name="see-also"></a>См. также
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)