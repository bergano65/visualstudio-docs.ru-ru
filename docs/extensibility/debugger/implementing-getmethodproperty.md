---
title: Реализация GetMethodProperty | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetMethodProperty method
- IDebugExpressionEvaluator2 property
ms.assetid: 6305874f-a2c4-4432-834c-07530ea84bff
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 86dea630dc4f04a96cf017d6ac203441c71dedf5
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55031946"
---
# <a name="implement-getmethodproperty"></a>Реализация GetMethodProperty
> [!IMPORTANT]
>  В Visual Studio 2015 таким образом, реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [образец средства оценки выражений управляемый](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Visual Studio вызывает отладки ядра (DE) [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md), который в свою очередь вызывает [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) для получения сведений о текущем методе в кадре стека.  
  
 Эта реализация `IDebugExpressionEvaluator::GetMethodProperty` выполняет следующие задачи:  
  
1.  Вызовы [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md), передавая [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) объекта. Возвращает поставщик символов (SP) [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) предоставляющий метод, который содержит указанный адрес.  
  
2.  Получает [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) из `IDebugContainerField`.  
  
3.  Создает экземпляр класса (называется `CFieldProperty` в этом примере), реализующий [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) интерфейс, а также содержит `IDebugMethodField` объект, возвращенный верификации поставщиком услуг, выполните следующие действия.  
  
4.  Возвращает `IDebugProperty2` интерфейс из `CFieldProperty` объекта.  
  
## <a name="managed-code"></a>Управляемый код  
 В этом примере показана реализация `IDebugExpressionEvaluator::GetMethodProperty` в управляемом коде.  
  
```csharp  
namespace EEMC  
{  
    [GuidAttribute("462D4A3D-B257-4AEE-97CD-5918C7531757")]  
    public class EEMCClass : IDebugExpressionEvaluator  
    {  
        public HRESULT GetMethodProperty(  
                IDebugSymbolProvider symbolProvider,  
                IDebugAddress        address,  
                IDebugBinder         binder,  
                int                  includeHiddenLocals,  
            out IDebugProperty2      property)   
        {  
            IDebugContainerField containerField = null;  
            IDebugMethodField methodField       = null;  
            property = null;  
  
            // Get the containing method field.  
            symbolProvider.GetContainerField(address, out containerField);  
            methodField = (IDebugMethodField) containerField;  
  
            // Return the property of method field.  
            property = new CFieldProperty(symbolProvider, address, binder, methodField);  
            return COM.S_OK;  
        }  
    }  
}  
```  
  
## <a name="unmanaged-code"></a>Неуправляемый код  
 В этом примере показана реализация `IDebugExpressionEvaluator::GetMethodProperty` в неуправляемом коде.  
  
```  
[CPP]  
STDMETHODIMP CExpressionEvaluator::GetMethodProperty(  
        in IDebugSymbolProvider *pprovider,  
        in IDebugAddress        *paddress,  
        in IDebugBinder         *pbinder,  
        in BOOL                  includeHiddenLocals,  
        out IDebugProperty2    **ppproperty  
    )  
{  
    if (pprovider == NULL)  
        return E_INVALIDARG;  
  
    if (ppproperty == NULL)  
        return E_INVALIDARG;  
    else  
        *ppproperty = 0;  
  
    HRESULT hr;  
    IDebugContainerField* pcontainer = NULL;  
  
    hr = pprovider->GetContainerField(paddress, &pcontainer);  
    if (FAILED(hr))  
        return hr;  
  
    IDebugMethodField*    pmethod    = NULL;  
    hr = pcontainer->QueryInterface( IID_IDebugMethodField,  
            reinterpret_cast<void**>(&pmethod));  
    pcontainer->Release();  
    if (FAILED(hr))  
        return hr;  
  
    CFieldProperty* pfieldProperty = new CFieldProperty( pprovider,  
                                                         paddress,  
                                                         pbinder,  
                                                         pmethod );  
    pmethod->Release();  
    if (!pfieldProperty)  
        return E_OUTOFMEMORY;  
  
    hr = pfieldProperty->Init();  
    if (FAILED(hr))  
    {  
        pfieldProperty->Release();  
        return hr;  
    }  
  
    hr = pfieldProperty->QueryInterface( IID_IDebugProperty2,  
            reinterpret_cast<void**>(ppproperty));  
    pfieldProperty->Release();  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>См. также  
 [Пример реализации локальных переменных](../../extensibility/debugger/sample-implementation-of-locals.md)