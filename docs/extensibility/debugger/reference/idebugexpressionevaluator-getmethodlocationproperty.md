---
title: IDebugExpressionEvaluator::GetMethodLocationProperty | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty method
ms.assetid: 52c42a2e-f144-476b-8bef-442464c8fe8e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: faa2767e54e9821c7b3270fa60f5be232a2c232f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66325767"
---
# <a name="idebugexpressionevaluatorgetmethodlocationproperty"></a>IDebugExpressionEvaluator::GetMethodLocationProperty
Этот метод преобразует метод расположение и смещение в адрес памяти.

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
[in] Метод расположение и смещение, выраженное в виде строки.

`pSymbolProvider`\
[in] Поставщик символов выражается [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) объекта.

`pAddress`\
[in] Адрес в методе, выраженное как [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) объекта.

`pBinder`\
[in] Связыватель выражается [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) объекта.

`ppProperty`\
[out] Возвращает [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) интерфейс, который представляет собой адрес памяти.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Возвращаемый адрес можно использовать для задания точки останова, например.

 Несмотря на название `upstrFullyQualifiedMethodPlusOffset`, этот параметр можно передать имя метода частичных. В этом случае выбранного метода является тот, который заключает `pAddress`. Способ интерпретации этот параметр зависит от реализации средство оценки выражений и язык, который поддерживается.

## <a name="see-also"></a>См. также
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)