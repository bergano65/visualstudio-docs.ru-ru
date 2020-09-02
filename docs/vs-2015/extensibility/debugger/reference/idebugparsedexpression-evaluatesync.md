---
title: 'Идебугпарседекспрессион:: Евалуатесинк | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugParsedExpression::EvaluateSync
helpviewer_keywords:
- IDebugParsedExpression::EvaluateSync method
ms.assetid: 0ea04cfa-de87-4b6c-897e-4572c1a28942
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6761cd5ec9df67d511ab905e173ac0f286c5ee7d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194552"
---
# <a name="idebugparsedexpressionevaluatesync"></a>IDebugParsedExpression::EvaluateSync
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот метод вычисляет проанализированное выражение и при необходимости приводит результат к другому типу данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT EvaluateSync(   
   DWORD                 dwEvalFlags,  
   DWORD                 dwTimeout,  
   IDebugSymbolProvider* pSymbolProvider,  
   IDebugAddress*        pAddress,  
   IDebugBinder*         pBinder,  
   BSTR                  bstrResultType,  
   IDebugProperty2**     ppResult  
);  
```  
  
```csharp  
int EvaluateSync(  
   uint                 dwEvalFlags,   
   uint                 dwTimeout,   
   IDebugSymbolProvider pSymbolProvider,   
   IDebugAddress        pAddress,   
   IDebugBinder         pBinder,   
   string               bstrResultType,   
   out IDebugProperty2  ppResult  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwEvalFlags`  
 окне Сочетание констант [евалфлагс](../../../extensibility/debugger/reference/evalflags.md) , определяющих способ вычисления выражения.  
  
 `dwTimeout`  
 окне Указывает максимальное время ожидания (в миллисекундах) перед возвратом из этого метода. Используйте `INFINITE` для бесконечного ожидания.  
  
 `pSymbolProvider`  
 окне Поставщик символов, выраженный в виде интерфейса [идебугсимболпровидер](../../../extensibility/debugger/reference/idebugsymbolprovider.md) .  
  
 `pAddress`  
 окне Текущее место выполнения в методе, выраженное как интерфейс [идебугаддресс](../../../extensibility/debugger/reference/idebugaddress.md) .  
  
 `pBinder`  
 окне Связыватель, выраженный в виде интерфейса [идебугбиндер](../../../extensibility/debugger/reference/idebugbinder.md) .  
  
 `bstrResultType`  
 окне Тип результата, к которому должен быть приведен результат. Этот аргумент может иметь значение null.  
  
 `ppResult`  
 заполняет Возвращает интерфейс [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , представляющий результаты вычисления.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Контекст вычисления выражения предоставляется методом `pAddress` , который позволяет определить содержащий метод, а затем использовать правила определения области языка, чтобы определить значение символов в выражении.  
  
## <a name="see-also"></a>См. также:  
 [идебугсимболпровидер](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [идебугбиндер](../../../extensibility/debugger/reference/idebugbinder.md)   
 [идебугаддресс](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)
