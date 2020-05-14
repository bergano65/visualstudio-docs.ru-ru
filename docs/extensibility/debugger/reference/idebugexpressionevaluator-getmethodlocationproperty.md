---
title: IDebugExpressionОдиорОценор::GetMethodLocationНедвижимость (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty method
ms.assetid: 52c42a2e-f144-476b-8bef-442464c8fe8e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a6ba87d6c1a1f7370ce5e209440589f362b87035
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729520"
---
# <a name="idebugexpressionevaluatorgetmethodlocationproperty"></a>IDebugExpressionEvaluator::GetMethodLocationProperty
Этот метод преобразует местоположение метода и компенсируется в адрес памяти.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetMethodLocationProperty( 
   LPCOLESTR             upstrFullyQualifiedMethodPlusOffset,
   IDebugSymbolProvider* pSymbolProvider,
   IDebugAddress*        pAddress,
   IDebugBinder*         pBinder,
   IDebugProperty2**     ppProperty
);
```

```csharp
int GetMethodLocationProperty(
   string               upstrFullyQualifiedMethodPlusOffset,
   IDebugSymbolProvider pSymbolProvider,
   IDebugAddress        pAddress,
   IDebugBinder         pBinder,
   out IDebugProperty2  ppProperty
);
```

## <a name="parameters"></a>Параметры
`upstrFullyQualifiedMethodPlusOffset`\
(в) Расположение метода и смещение, выраженное как строка.

`pSymbolProvider`\
(в) Поставщик символов выражается как объект [IDebugSymbolProvider.](../../../extensibility/debugger/reference/idebugsymbolprovider.md)

`pAddress`\
(в) Адрес в методе, выраженный как объект [IDebugAddress.](../../../extensibility/debugger/reference/idebugaddress.md)

`pBinder`\
(в) Связующего выраженного как объект [IDebugBinder.](../../../extensibility/debugger/reference/idebugbinder.md)

`ppProperty`\
(ваут) Возвращает интерфейс [IDebugProperty2,](../../../extensibility/debugger/reference/idebugproperty2.md) представляющий адрес памяти.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Например, возвращенный адрес можно использовать для установки точки разрыва.

 Несмотря `upstrFullyQualifiedMethodPlusOffset`на название, этот параметр может быть пройден частично квалифицированным названием метода. В этом случае выбранный метод заключается в `pAddress`том, что он заключается в. То, как интерпретируется этот параметр, до реализации оценщика выражения и языка, который он поддерживает.

## <a name="see-also"></a>См. также
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
