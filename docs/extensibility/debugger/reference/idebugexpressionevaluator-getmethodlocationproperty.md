---
title: IDebugExpressionEvaluator::GetMethodLocationProperty | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty method
ms.assetid: 52c42a2e-f144-476b-8bef-442464c8fe8e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c15baa5475e912559b8cc0a23264b0c19ef8a464
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56686734"
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

#### <a name="parameters"></a>Параметры
 `upstrFullyQualifiedMethodPlusOffset`

 [in] Метод расположение и смещение, выраженное в виде строки.

 `pSymbolProvider`

 [in] Поставщик символов выражается [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) объекта.

 `pAddress`

 [in] Адрес в методе, выраженное как [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) объекта.

 `pBinder`

 [in] Связыватель выражается [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) объекта.

 `ppProperty`

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