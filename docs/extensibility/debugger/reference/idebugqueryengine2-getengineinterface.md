---
title: IDebugQueryEngine2::GetEngineInterface | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugQueryEngine2::GetEngineInterface
helpviewer_keywords:
- IDebugQueryEngine2::GetEngineInterface
ms.assetid: ed84aa98-7ec7-48f3-97ae-821090bc3664
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c720ac348179ec979ba1ffbc1488244ca69246c4
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66339930"
---
# <a name="idebugqueryengine2getengineinterface"></a>IDebugQueryEngine2::GetEngineInterface
Получает интерфейс отладки ядра (DE).

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetEngineInterface( 
   IUnknown** ppUnk
);
```

```csharp
int GetEngineInterface( 
   out object ppUnk
);
```

## <a name="parameters"></a>Параметры
`ppUnk`\
[out] Возвращает `IUnknown` объект представляет модуль отладки (DE), и который можно запросить для любого другого допустимым интерфейса, связанные с Развернутой (например [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) или [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)).

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Итоговый интерфейс следует использовать с осторожностью, так как вызов через интерфейсы, полученные из этого метода позволяет обойти диспетчер отладки сеансов обработки и может привести к SDM в некорректном состоянии или вызвали ошибку во время отладки.

## <a name="see-also"></a>См. также
- [IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)