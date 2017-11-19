---
title: "Оценка контрольное выражение | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- expression evaluation, watch expressions
- watch expressions
ms.assetid: 8317cd52-6fea-4e8f-a739-774dc06bd44b
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0dfc63e378766fa6b50e52788d7117d767613bec
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="evaluating-a-watch-expression"></a>Вычисление выражения Контрольное значение
> [!IMPORTANT]
>  В Visual Studio 2015 этот способ реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Если Visual Studio готов для отображения значения контрольное выражение, он вызывает [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) в свою очередь вызывает [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). В результате получается [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) объект, содержащий значение и тип выражения.  
  
 В этой реализации `IDebugParsedExpression::EvaluateSync`, выражение анализируется и оценивается в то же время. Эта реализация выполняет следующие задачи:  
  
1.  Выполняет синтаксический анализ и вычисляет выражение для создания универсальный объект, который содержит значения и его тип. В C# это представляется как `object` хотя в C++ это представляется как `VARIANT`.  
  
2.  Создает экземпляр класса (называется `CValueProperty` в этом примере), реализующий `IDebugProperty2` интерфейс и сохраняет в классе возвращаемого значения.  
  
3.  Возвращает `IDebugProperty2` интерфейс из `CValueProperty` объекта.  
  
## <a name="managed-code"></a>Управляемый код  
 Это реализация `IDebugParsedExpression::EvaluateSync` в управляемом коде. Вспомогательный метод `Tokenize` выполняет синтаксический анализ выражения в дерево синтаксического анализа. Вспомогательная функция `EvalToken` преобразуется в значение токена. Вспомогательная функция `FindTerm` рекурсивно проходит через дерево синтаксического анализа, вызов `EvalToken` для каждого узла, представляющее значение и применение любые операции (сложение или вычитание) в выражении.  
  
```csharp  
namespace EEMC  
{  
    public class CParsedExpression : IDebugParsedExpression  
    {  
        public HRESULT EvaluateSync(  
            uint evalFlags,  
            uint timeout,  
            IDebugSymbolProvider provider,  
            IDebugAddress address,  
            IDebugBinder binder,  
            string resultType,  
            out IDebugProperty2 result)  
        {  
            HRESULT retval = COM.S_OK;  
            this.evalFlags = evalFlags;  
            this.timeout = timeout;  
            this.provider = provider;  
            this.address = address;  
            this.binder = binder;  
            this.resultType = resultType;  
  
            try  
            {  
                IDebugField field = null;  
                // Tokenize, then parse.  
                tokens = Tokenize(expression);  
                result = new CValueProperty(  
                             expression,  
                             (int) FindTerm(EvalToken(tokens[0], out field),1),  
                             field,  
                             binder);  
            }  
            catch (ParseException)  
            {  
                result = new CValueProperty(expression, "Huh?");  
                retval = COM.E_INVALIDARG;  
            }  
            return retval;  
        }  
    }  
}  
```  
  
## <a name="unmanaged-code"></a>Неуправляемый код  
 Это реализация `IDebugParsedExpression::EvaluateSync` в неуправляемом коде. Вспомогательная функция `Evaluate` выполняет синтаксический анализ и вычисляет выражение, возвращая `VARIANT` удержание результирующего значения. Вспомогательная функция `VariantValueToProperty` пакетов `VARIANT` в `CValueProperty` объекта.  
  
```  
[C++]  
STDMETHODIMP CParsedExpression::EvaluateSync(   
    in  DWORD                 evalFlags,  
    in  DWORD                 dwTimeout,  
    in  IDebugSymbolProvider* pprovider,  
    in  IDebugAddress*        paddress,  
    in  IDebugBinder*         pbinder,  
    in  BSTR                  bstrResultType,  
    out IDebugProperty2**     ppproperty )  
{  
    // dwTimeout parameter is ignored in this implementation.  
    if (pprovider == NULL)  
        return E_INVALIDARG;  
  
    if (paddress == NULL)  
        return E_INVALIDARG;  
  
    if (pbinder == NULL)  
        return E_INVALIDARG;  
  
    if (ppproperty == NULL)  
        return E_INVALIDARG;  
    else  
        *ppproperty = 0;  
  
    HRESULT hr;  
    VARIANT value;  
    BSTR    bstrErrorMessage = NULL;  
    hr = ::Evaluate( pprovider,  
                     paddress,  
                     pbinder,  
                     m_expr,  
                     &bstrErrorMessage,  
                     &value );  
    if (hr != S_OK)  
    {  
        if (bstrErrorMessage == NULL)  
            return hr;  
  
        //we can display better messages ourselves.  
        HRESULT hrLocal = S_OK;  
        VARIANT varType;  
        VARIANT varErrorMessage;  
  
        VariantInit( &varType );  
        VariantInit( &varErrorMessage );  
        varErrorMessage.vt      = VT_BSTR;  
        varErrorMessage.bstrVal = bstrErrorMessage;  
  
        CValueProperty* valueProperty = new CValueProperty();  
        if (valueProperty != NULL)  
        {  
            hrLocal = valueProperty->Init(m_expr, varType, varErrorMessage);  
            if (SUCCEEDED(hrLocal))   
            {  
                hrLocal = valueProperty->QueryInterface( IID_IDebugProperty2,  
                        reinterpret_cast<void**>(ppproperty) );  
            }  
        }  
  
        VariantClear(&varType);  
        VariantClear(&varErrorMessage); //frees BSTR  
        if (!valueProperty)  
            return hr;  
        valueProperty->Release();  
        if (FAILED(hrLocal))  
            return hr;  
    }  
    else  
    {  
        if (bstrErrorMessage != NULL)  
            SysFreeString(bstrErrorMessage);  
  
        hr = VariantValueToProperty( pprovider,  
                                     paddress,  
                                     pbinder,  
                                     m_radix,  
                                     m_expr,  
                                     value,  
                                     ppproperty );  
        VariantClear(&value);  
        if (FAILED(hr))  
            return hr;  
    }  
  
    return S_OK;  
}  
```  
  
## <a name="see-also"></a>См. также  
 [Оценки выражения окна контрольных значений](../../extensibility/debugger/evaluating-a-watch-window-expression.md)   
 [Пример реализации вычисления выражений](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)