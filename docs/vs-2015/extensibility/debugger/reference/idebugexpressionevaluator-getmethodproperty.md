---
title: 'Идебужекспрессионевалуатор:: Жетмесодпроперти | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::GetMethodProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodProperty method
ms.assetid: c394fe4d-eeb6-4feb-828c-098d84a6f1ba
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b84ac959241a8f68f4d9516879660b6414708731
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155353"
---
# <a name="idebugexpressionevaluatorgetmethodproperty"></a>IDebugExpressionEvaluator::GetMethodProperty
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот метод возвращает объект Property, содержащий локальные переменные, аргументы и другие свойства метода.  
  
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
 окне Используемый поставщик символов, выраженный как объект [идебугсимболпровидер](../../../extensibility/debugger/reference/idebugsymbolprovider.md) .  
  
 `pAddress`  
 окне Адрес в коде, выраженный как объект [идебугаддресс](../../../extensibility/debugger/reference/idebugaddress.md) , который должен быть разрешаться в ближайшую содержащую функцию.  
  
 `pBinder`  
 окне Используемый связыватель, выраженный как объект [идебугбиндер](../../../extensibility/debugger/reference/idebugbinder.md) .  
  
 `fIncludeHiddenLocals`  
 окне Ненулевое ( `TRUE` ) означает включение скрытых локальных переменных; нуль ( `FALSE` ) означает выход из скрытых локальных переменных  
  
 `ppProperty`  
 заполняет Возвращает объект [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , представляющий метод.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Скрытые локальные переменные обычно являются переменными, создаваемыми компилятором.  
  
## <a name="see-also"></a>См. также:  
 [идебужекспрессионевалуатор](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)   
 [идебугсимболпровидер](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [идебугаддресс](../../../extensibility/debugger/reference/idebugaddress.md)   
 [идебугбиндер](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
