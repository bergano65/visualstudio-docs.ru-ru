---
title: IDebugExpressionContext2::ParseText | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugExpressionContext2::ParseText
helpviewer_keywords:
- IDebugExpressionContext2::ParseText
ms.assetid: f58575db-f926-4ac8-83ff-7b3b86ab61e2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e95a8a76e7315f8963ea415f88bd9615f3b123a4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idebugexpressioncontext2parsetext"></a>IDebugExpressionContext2::ParseText
Выполняет синтаксический анализ выражения в виде текста для дальнейшего определения.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT ParseText(   
   LPCOLESTR           pszCode,  
   PARSEFLAGS          dwFlags,  
   UINT                nRadix,  
   IDebugExpression2** ppExpr,  
   BSTR*               pbstrError,  
   UINT*               pichError  
);  
```  
  
```csharp  
int ParseText(   
   string                pszCode,  
   enum_PARSEFLAGS       dwFlags,  
   uint                  nRadix,  
   out IDebugExpression2 ppExpr,  
   out string            pbstrError,  
   out uint              pichError  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pszCode`  
 [in] Выражение может быть проанализирован.  
  
 `dwFlags`  
 [in] Сочетание флагов из [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md) перечисления, который управляет синтаксического анализа.  
  
 `nRadix`  
 [in] Основание системы счисления для использования при анализе все числовые данные в `pszCode`.  
  
 `ppExpr`  
 [out] Возвращает [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) , представляющий проанализированный выражения, которое будет готов для привязки и оценки.  
  
 `pbstrError`  
 [out] Возвращает сообщение об ошибке, если выражение содержит ошибку.  
  
 `pichError`  
 [out] Возвращает индекс символа ошибки в `pszCode` Если выражение содержит ошибку.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 При вызове этого метода модуля отладки (DE) следует синтаксический анализ выражения и проверить его правильность. `pbstrError` И `pichError` параметров может быть заполнен, если выражение является недопустимым.  
  
 Обратите внимание, что выражение не вычисляется, только синтаксический анализ. Последующий вызов [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) или [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) методы вычисляет проанализированное выражение.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как реализовать этот метод для простой `CEnvBlock` объекта, который предоставляет [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) интерфейса. В этом примере считает, что выражение может быть проанализирован как имя переменной среды и возвращает значение этой переменной.  
  
```cpp  
HRESULT CEnvBlock::ParseText(  
   LPCOLESTR           pszCode,  
   PARSEFLAGS          dwFlags,  
   UINT                nRadix,  
   IDebugExpression2 **ppExpr,  
   BSTR               *pbstrError,  
   UINT               *pichError)  
{  
   HRESULT hr = E_OUTOFMEMORY;    
   // Create an integer variable with a value equal to one plus    
   // twice the length of the passed expression to be parsed.    
   int iAnsiLen      = 2 * (wcslen(pszCode)) + 1;    
   // Allocate a character string of the same length.    
   char *pszAnsiCode = (char *) malloc(iAnsiLen);    
  
   // Check for successful memory allocation.    
   if (pszAnsiCode) {    
      // Map the wide-character pszCode string to the new pszAnsiCode character string.    
      WideCharToMultiByte(CP_ACP, 0, pszCode, -1, pszAnsiCode, iAnsiLen, NULL, NULL);    
      // Check to see if the app can succesfully get the environment variable.    
      if (GetEnv(pszAnsiCode)) {    
  
         // Create and initialize a CExpression object.    
         CComObject<CExpression> *pExpr;    
         CComObject<CExpression>::CreateInstance(&pExpr);    
            pExpr->Init(pszAnsiCode, this, NULL);    
  
         // Assign the pointer to the new object to the passed argument  
         // and AddRef the object.    
         *ppExpr = pExpr;    
         (*ppExpr)->AddRef();    
         hr = S_OK;    
      // If the program cannot succesfully get the environment variable.    
      } else {    
         // Set the errror message and return E_FAIL.    
         *pbstrError = SysAllocString(L"No such environment variable.");    
         hr = E_FAIL;    
      }    
      // Free the local character string.    
      free(pszAnsiCode);    
   }    
   return hr;    
}    
```  
  
## <a name="see-also"></a>См. также  
 [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)   
 [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)   
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)