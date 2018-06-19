---
title: IDebugExpressionEvaluator::Parse | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugExpressionEvaluator::Parse
helpviewer_keywords:
- IDebugExpressionEvaluator::Parse method
ms.assetid: e6e31b3a-63a7-4293-bcda-267eb78dffb6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2a10a65564682b5c82350eb5c22af3f217a3a993
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31110807"
---
# <a name="idebugexpressionevaluatorparse"></a>IDebugExpressionEvaluator::Parse
Этот метод преобразует строку выражения проанализированный выражение.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT Parse(   
   LPCOLESTR                upstrExpression,  
   PARSEFLAGS               dwFlags,  
   UINT                     nRadix,  
   BSTR*                    pbstrError,  
   UINT*                    pichError,  
   IDebugParsedExpression** ppParsedExpression  
);  
```  
  
```csharp  
int Parse(  
   string                     upstrExpression,   
   enum_PARSEFLAGS            dwFlags,   
   uint                       nRadix,   
   out string                 pbstrError,   
   out uint                   pichError,   
   out IDebugParsedExpression ppParsedExpression  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `upstrExpression`  
 [in] Строка выражения для синтаксического анализа.  
  
 `dwFlags`  
 [in] Коллекция [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md) константы, которые определяют, как выполнить синтаксический анализ выражения.  
  
 `nRadix`  
 [in] Основание системы счисления, используемое для интерпретации все числовые данные.  
  
 `pbstrError`  
 [out] Возвращает ошибку в виде удобочитаемого текста.  
  
 `pichError`  
 [out] Возвращает позицию символа начинается ошибка в строке выражения.  
  
 `ppParsedExpression`  
 [out] Возвращает выражение, проанализированных в [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) объекта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод создает проанализированное выражение не фактического значения. Проанализированное выражение готовое к вычислению, то есть, преобразуется в значение.  
  
## <a name="see-also"></a>См. также  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)   
 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)   
 [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)