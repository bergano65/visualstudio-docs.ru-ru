---
title: IDebugExpressionEvaluator::Parse | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::Parse
helpviewer_keywords:
- IDebugExpressionEvaluator::Parse method
ms.assetid: e6e31b3a-63a7-4293-bcda-267eb78dffb6
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4039534b139eeeaf20f938c6d6c358c602f96227
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58992379"
---
# <a name="idebugexpressionevaluatorparse"></a>IDebugExpressionEvaluator::Parse
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот метод преобразует строку выражения проанализированное выражение.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 [in] Строка выражения, который необходимо проанализировать.  
  
 `dwFlags`  
 [in] Коллекция [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md) константы, которые определяют, как выражение для синтаксического анализа.  
  
 `nRadix`  
 [in] Основание системы счисления для использования для интерпретации все числовые данные.  
  
 `pbstrError`  
 [out] Возвращает ошибку в виде удобочитаемого текста.  
  
 `pichError`  
 [out] Возвращает позицию символа начинается ошибка в строке выражения.  
  
 `ppParsedExpression`  
 [out] Возвращает проанализированное выражение в [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) объекта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод создает проанализированное выражение, а не фактического значения. Проанализированное выражение готов для вычисления, то есть преобразовать в значение.  
  
## <a name="see-also"></a>См. также  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)   
 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)   
 [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)
