---
title: IDebugExpressionEvaluator3::Parse2 | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugExpressionEvaluator3::Parse2
ms.assetid: 78099628-d600-4f76-b7c8-ee07c864af1e
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 79dc8f28d101a2c7bdd9749dcd9b3dadb4204273
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47569348"
---
# <a name="idebugexpressionevaluator3parse2"></a>IDebugExpressionEvaluator3::Parse2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugExpressionEvaluator3::Parse2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugexpressionevaluator3-parse2).  
  
Преобразует строку выражения проанализированное выражение с учетом поставщик символов и адрес оценке кадра.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT Parse2 (  
   LPCOLESTR                upstrExpression,  
   PARSEFLAGS               dwFlags,  
   UINT                     nRadix,  
   IDebugSymbolProvider*    pSymbolProvider,  
   IDebugAddress*           pAddress,  
   BSTR*                    pbstrError,  
   UINT*                    pichError,  
   IDebugParsedExpression** ppParsedExpression  
);  
```  
  
```csharp  
HRESULT Parse2 (  
   string                     upstrExpression,  
   enum_PARSEFLAGS            dwFlags,  
   uint                       nRadix,  
   IDebugSymbolProvider       pSymbolProvider,  
   IDebugAddress              pAddress,  
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
  
 `pSymbolProvider`  
 [in] Интерфейс поставщика символов.  
  
 `pAddress`  
 [in] Адрес оценке кадра.  
  
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
  
## <a name="example"></a>Пример  
 В следующем примере показано, как реализовать этот метод для **CEE** объекта, который предоставляет [IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md) интерфейс.  
  
```cpp#  
HRESULT CEE::Parse2 ( LPCOLESTR in_szExprText,  
  PARSEFLAGS in_FLAGS,  
  UINT in_RADIX,  
  IDebugSymbolProvider *pSymbolProvider,  
  IDebugAddress *pAddress,  
  BSTR* out_pbstrError,  
  UINT* inout_pichError,  
  IDebugParsedExpression** out_ppParsedExpression )  
{  
    // precondition  
    REQUIRE( NULL != in_szExprText );  
    //REQUIRE( NULL != out_pbstrError );  
    REQUIRE( NULL != inout_pichError );  
    REQUIRE( NULL != out_ppParsedExpression );  
  
    if (NULL == in_szExprText)  
        return E_INVALIDARG;  
  
    if (NULL == inout_pichError)  
        return E_POINTER;  
  
    if (NULL == out_ppParsedExpression)  
        return E_POINTER;  
  
    if (out_pbstrError)  
        *out_pbstrError = NULL;  
  
    *out_ppParsedExpression = NULL;  
  
    INVARIANT( this );  
  
    if (!this->ClassInvariant())  
        return E_UNEXPECTED;  
  
    // function body  
    EEDomain::fParseExpression DomainVal =  
    {  
        this,                   // CEE*  
        in_szExprText,          // LPCOLESTR  
        in_FLAGS,               // EVALFLAGS  
        in_RADIX,               // RADIX  
        out_pbstrError      ,   // BSTR*  
        inout_pichError,        // UINT*  
        pSymbolProvider,  
        out_ppParsedExpression  // Output  
    };  
  
    return (*m_LanguageSpecificUseCases.pfParseExpression)(DomainVal);  
}  
```  
  
## <a name="see-also"></a>См. также  
 [IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)

