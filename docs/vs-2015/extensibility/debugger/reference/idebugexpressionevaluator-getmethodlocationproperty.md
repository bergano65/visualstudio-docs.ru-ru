---
title: 'Идебужекспрессионевалуатор:: Жетмесодлокатионпроперти | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty method
ms.assetid: 52c42a2e-f144-476b-8bef-442464c8fe8e
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d82b002d9253b2d48f78e74fdf964cf42d241d9a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68144394"
---
# <a name="idebugexpressionevaluatorgetmethodlocationproperty"></a>IDebugExpressionEvaluator::GetMethodLocationProperty
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот метод преобразует расположение метода и смещение в адрес памяти.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 окне Положение и смещение метода, выраженное в виде строки.  
  
 `pSymbolProvider`  
 окне Поставщик символов, выраженный в виде объекта [идебугсимболпровидер](../../../extensibility/debugger/reference/idebugsymbolprovider.md) .  
  
 `pAddress`  
 окне Адрес в методе, выраженный как объект [идебугаддресс](../../../extensibility/debugger/reference/idebugaddress.md) .  
  
 `pBinder`  
 окне Связыватель, выраженный как объект [идебугбиндер](../../../extensibility/debugger/reference/idebugbinder.md) .  
  
 `ppProperty`  
 заполняет Возвращает интерфейс [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , представляющий адрес памяти.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Для задания точки останова можно использовать возвращенный адрес, например.  
  
 Несмотря на имя `upstrFullyQualifiedMethodPlusOffset` , этому параметру может быть передано имя метода с частичным указанием. В этом случае выбранным методом является тот, который в нем заключен `pAddress` . Способ интерпретации этого параметра является реализацией средства оценки выражений и поддерживаемого им языка.  
  
## <a name="see-also"></a>См. также:  
 [идебугсимболпровидер](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [идебугбиндер](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
