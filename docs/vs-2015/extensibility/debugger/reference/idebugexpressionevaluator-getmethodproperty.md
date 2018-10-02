---
title: IDebugExpressionEvaluator::GetMethodProperty | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugExpressionEvaluator::GetMethodProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodProperty method
ms.assetid: c394fe4d-eeb6-4feb-828c-098d84a6f1ba
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: def1f66be288574dc27af3b4685a008eb0c14ee3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47559098"
---
# <a name="idebugexpressionevaluatorgetmethodproperty"></a>IDebugExpressionEvaluator::GetMethodProperty
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugExpressionEvaluator::GetMethodProperty](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty).  
  
Этот метод возвращает объект свойства, содержит локальные переменные, аргументы и другие свойства для метода.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
  
#### <a name="parameters"></a>Параметры  
 `pSymbolProvider`  
 [in] Поставщик символов для использования, выраженное как [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) объекта.  
  
 `pAddress`  
 [in] Адрес в коде, выраженное как [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) объекта, который должно быть разрешено в ближайшей, содержащую функцию.  
  
 `pBinder`  
 [in] Связыватель для использования, выраженное как [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) объекта.  
  
 `fIncludeHiddenLocals`  
 [in] Ненулевое значение (`TRUE`) означает, что для включения скрытых локальных переменных; ноль (`FALSE`) означает, что убрать скрытых "Локальные"  
  
 `ppProperty`  
 [out] Возвращает [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) объект, представляющий метод.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Скрытые "Локальные" обычно являются переменными, создаваемых компилятором.  
  
## <a name="see-also"></a>См. также  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)   
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)

