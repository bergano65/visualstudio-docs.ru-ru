---
title: IDebugExpressionО-оценщик::GetMethodProperty Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::GetMethodProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodProperty method
ms.assetid: c394fe4d-eeb6-4feb-828c-098d84a6f1ba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ebcf24ee39505091ff79c1f2f31d505217f77efb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729508"
---
# <a name="idebugexpressionevaluatorgetmethodproperty"></a>IDebugExpressionEvaluator::GetMethodProperty
Этот метод получает объект свойства, содержащий местных жителей, аргументы и другие свойства метода.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetMethodProperty( 
   IDebugSymbolProvider* pSymbolProvider,
   IDebugAddress*        pAddress,
   IDebugBinder*         pBinder,
   BOOL                  fIncludeHiddenLocals,
   IDebugProperty2**     ppProperty
);
```

```csharp
int GetMethodProperty(
   IDebugSymbolProvider pSymbolProvider,
   IDebugAddress        pAddress,
   IDebugBinder         pBinder,
   int                  fIncludeHiddenLocals,
   out IDebugProperty2  ppProperty
);
```

## <a name="parameters"></a>Параметры
`pSymbolProvider`\
(в) Поставщик символов, который будет использоваться, выражается как объект [IDebugSymbolProvider.](../../../extensibility/debugger/reference/idebugsymbolprovider.md)

`pAddress`\
(в) Адрес в коде, выраженный как объект [IDebugAddress,](../../../extensibility/debugger/reference/idebugaddress.md) который должен быть решен до ближайшей функции, содержащей.

`pBinder`\
(в) Связующего, который будет использоваться, выраженный как объект [IDebugBinder.](../../../extensibility/debugger/reference/idebugbinder.md)

`fIncludeHiddenLocals`\
(в) Nonzero`TRUE`() означает включение скрытых местных жителей; ноль`FALSE`() означает оставить скрытые местные жители

`ppProperty`\
(ваут) Возвращает объект [IDebugProperty2,](../../../extensibility/debugger/reference/idebugproperty2.md) представляющий метод.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Скрытые местные жители, как правило, переменные, которые генерируются компилятором.

## <a name="see-also"></a>См. также
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
