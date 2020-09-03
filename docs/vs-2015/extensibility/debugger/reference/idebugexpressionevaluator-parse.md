---
title: Идебужекспрессионевалуатор::P Арсе | Документация Майкрософт
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155346"
---
# <a name="idebugexpressionevaluatorparse"></a>IDebugExpressionEvaluator::Parse
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот метод преобразует строку выражения в проанализированное выражение.  
  
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
 окне Строка выражения для синтаксического анализа.  
  
 `dwFlags`  
 окне Коллекция констант [парсефлагс](../../../extensibility/debugger/reference/parseflags.md) , определяющих способ синтаксического анализа выражения.  
  
 `nRadix`  
 окне Основание системы счисления, используемое для интерпретации любых числовых данных.  
  
 `pbstrError`  
 заполняет Возвращает ошибку в виде текста, читаемого человеком.  
  
 `pichError`  
 заполняет Возвращает позиции символа начала ошибки в строке выражения.  
  
 `ppParsedExpression`  
 заполняет Возвращает проанализированное выражение в объекте [идебугпарседекспрессион](../../../extensibility/debugger/reference/idebugparsedexpression.md) .  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Этот метод создает проанализированное выражение, а не фактическое значение. Проанализированное выражение готово к вычислению, то есть преобразованному в значение.  
  
## <a name="see-also"></a>См. также:  
 [идебужекспрессионевалуатор](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)   
 [идебугпарседекспрессион](../../../extensibility/debugger/reference/idebugparsedexpression.md)   
 [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)
