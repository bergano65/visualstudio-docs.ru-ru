---
title: IDebugFunctionObject::Оценка Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::Evaluate
helpviewer_keywords:
- IDebugFunctionObject::Evaluate method
ms.assetid: 29349ea3-d5c1-4135-aa76-ced073ab9683
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 529a5f67c808efa258bc0cb9899f546dbb90d431
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728507"
---
# <a name="idebugfunctionobjectevaluate"></a>IDebugFunctionObject::Evaluate
Вызывает функцию и возвращает полученное значение в качестве объекта.

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
(в) Массив объектов [IDebugObject,](../../../extensibility/debugger/reference/idebugobject.md) представляющих параметры ввода. Каждый из этих параметров был `Create` создан с помощью одного из методов в интерфейсе [IDebugFunction.](../../../extensibility/debugger/reference/idebugfunctionobject.md)

`dwParams`\
(в) Количество параметров в `ppParams` массиве.

`dwTimeout`\
(в) Определяет максимальное время, в миллисекундах, чтобы ждать, прежде чем вернуться из этого метода. Используйте, `INFINITE` чтобы ждать бесконечно.

`ppResult`\
(ваут) Возвращает [IDebugObject,](../../../extensibility/debugger/reference/idebugobject.md) представляющий значение функции как объекта.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха, возвращается S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Этот метод настраивает и выполняет вызов функции, представленной объектом [IDebugFunction.](../../../extensibility/debugger/reference/idebugfunctionobject.md)

## <a name="see-also"></a>См. также
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
