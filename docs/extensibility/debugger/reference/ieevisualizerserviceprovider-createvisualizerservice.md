---
title: IEEVisualizerServiceProvider::CreateVisualizerService Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService
helpviewer_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService method
ms.assetid: f366f7c9-358d-46c8-993f-32ff86539833
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e05677122b7d4e4eb025a9382ede1509374de894
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717916"
---
# <a name="ieevisualizerserviceprovidercreatevisualizerservice"></a>IEEVisualizerServiceProvider::CreateVisualizerService
Этот метод создает услугу визуализатора.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT CreateVisualizerService(
   IDebugBinder*              binder,
   IDebugSymbolProvider*      pSymProv,
   IDebugAddress*             pAddress,
   IEEVisualizerDataProvider* dataProvider,
   IEEVisualizerService**     ppService
);
```

```csharp
int CreateVisualizerService(
   IDebugBinder binder,
   IDebugSymbolProvider      pSymProv,
   IDebugAddress             pAddress,
   IEEVisualizerDataProvider dataProvider,
   out IEEVisualizerService  ppService
);
```

## <a name="parameters"></a>Параметры
`binder`\
(в) Объект [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) перешел в [EvaluateSync.](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)

`pSymProv`\
(в) Объект [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) передан `IDebugParsedExpression::EvaluateSync`.

`pAddress`\
(в) Объект [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) передан `IDebugParsedExression::EvaluateSync`.

`dataProvider`\
(в) Объект, реализующий интерфейс [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) (поставляется оценщиком выражения).

`ppService`\
(ваут) Созданная служба.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 , `binder` `pSymProv`и `pAddress` параметры были переданы `IDebugParsedExpression::EvaluateSync` методу. `CreateVisualizerService`должен вызываться только `IDebugParsedExpression::EvaluateSync` из поддержки оценщика выражения для визуализаторов типов.

## <a name="see-also"></a>См. также
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
