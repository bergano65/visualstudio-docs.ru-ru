---
title: "IDebugParsedExpression::EvaluateSync | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugParsedExpression::EvaluateSync
helpviewer_keywords: IDebugParsedExpression::EvaluateSync method
ms.assetid: 0ea04cfa-de87-4b6c-897e-4572c1a28942
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7dbc17c9998be2d97e65452decf2ab97836e3128
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idebugparsedexpressionevaluatesync"></a>IDebugParsedExpression::EvaluateSync
Этот метод вычисления выражения проанализированный и при необходимости приводит результат к другому типу данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
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
 [in] Сочетание [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) константы, определяющие, как будет вычисляться выражение.  
  
 `dwTimeout`  
 [in] Указывает максимальное время (в миллисекундах) ожидания перед возвратом из этого метода. Используйте `INFINITE` для неограниченного времени ожидания.  
  
 `pSymbolProvider`  
 [in] Поставщик символа, выраженное [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) интерфейса.  
  
 `pAddress`  
 [in] Текущее положение выполнения внутри метода, выраженное [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) интерфейса.  
  
 `pBinder`  
 [in] Связыватель, выраженное [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) интерфейса.  
  
 `bstrResultType`  
 [in] Тип результата должен приводиться к. Этот аргумент может иметь значение null.  
  
 `ppResult`  
 [out] Возвращает [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) интерфейс, представляющий результаты оценки.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Контекст оценки выражения определяется `pAddress`, что позволяет определить, содержащий метод, и затем используйте области языка правил для определения значения символов в выражении.  
  
## <a name="see-also"></a>См. также  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)