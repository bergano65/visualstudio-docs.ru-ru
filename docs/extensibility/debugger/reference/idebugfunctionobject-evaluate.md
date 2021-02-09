---
title: 'Идебугфунктионобжект:: Evaluate | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::Evaluate
helpviewer_keywords:
- IDebugFunctionObject::Evaluate method
ms.assetid: 29349ea3-d5c1-4135-aa76-ced073ab9683
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 94285bc0ca36d4a55c3cd3a3483f6e20f6914271
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920979"
---
# <a name="idebugfunctionobjectevaluate"></a>IDebugFunctionObject::Evaluate
Вызывает функцию и возвращает результирующее значение в виде объекта.

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

## <a name="parameters"></a>Параметры
`ppParams`\
окне Массив объектов [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) , представляющих входные параметры. Каждый из этих параметров был создан с помощью одного из `Create` методов в интерфейсе [идебугфунктионобжект](../../../extensibility/debugger/reference/idebugfunctionobject.md) .

`dwParams`\
окне Число параметров в `ppParams` массиве.

`dwTimeout`\
окне Указывает максимальное время ожидания (в миллисекундах) перед возвратом из этого метода. Используйте `INFINITE` для бесконечного ожидания.

`ppResult`\
заполняет Возвращает [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) , представляющий значение функции в виде объекта.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Этот метод настраивает и выполняет вызов функции, представленной объектом [идебугфунктионобжект](../../../extensibility/debugger/reference/idebugfunctionobject.md) .

## <a name="see-also"></a>См. также раздел
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
