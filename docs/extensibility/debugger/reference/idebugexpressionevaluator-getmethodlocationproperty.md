---
title: IDebugExpressionEvaluator::GetMethodLocationProperty | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty method
ms.assetid: 52c42a2e-f144-476b-8bef-442464c8fe8e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f10a26eca06aed24d53b70cd406fe3f24e2fe898
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31111824"
---
# <a name="idebugexpressionevaluatorgetmethodlocationproperty"></a>IDebugExpressionEvaluator::GetMethodLocationProperty
Этот метод преобразует расположение метода и смещение в адрес памяти.  
  
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
 [in] Метод расположение и смещения, выраженное в виде строки.  
  
 `pSymbolProvider`  
 [in] Поставщик символ выражается [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) объекта.  
  
 `pAddress`  
 [in] Адрес в методе, выраженное [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) объекта.  
  
 `pBinder`  
 [in] Связыватель выражается [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) объекта.  
  
 `ppProperty`  
 [out] Возвращает [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) интерфейс, представляющий адрес в памяти.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Чтобы задать точку останова, например, можно использовать возвращенного адреса.  
  
 Несмотря на имя `upstrFullyQualifiedMethodPlusOffset`, этот параметр можно передать имя частичные метода. В этом случае выбранный метод именно эта заключает `pAddress`. Способ интерпретации этот параметр зависит от реализации средство оценки выражений и язык, который он поддерживает.  
  
## <a name="see-also"></a>См. также  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)