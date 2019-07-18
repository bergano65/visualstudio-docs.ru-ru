---
title: Реализация GetMethodProperty | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- GetMethodProperty method
- IDebugExpressionEvaluator2 property
ms.assetid: 6305874f-a2c4-4432-834c-07530ea84bff
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f125db668d240200e94539167381931898c75135
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63430304"
---
# <a name="implementing-getmethodproperty"></a>Реализация GetMethodProperty
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> В Visual Studio 2015 таким образом, реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Visual Studio вызывает отладки ядра (DE) [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md), который в свою очередь вызывает [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) для получения сведений о текущем методе в кадре стека.  
  
 Эта реализация `IDebugExpressionEvaluator::GetMethodProperty` выполняет следующие задачи:  
  
1. Вызовы [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md), передавая [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) объекта. Возвращает поставщик символов (SP) [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) предоставляющий метод, который содержит указанный адрес.  
  
2. Получает [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) из `IDebugContainerField`.  
  
3. Создает экземпляр класса (называется `CFieldProperty` в этом примере), реализующий [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) интерфейс, а также содержит `IDebugMethodField` объект, возвращенный верификации поставщиком услуг, выполните следующие действия.  
  
4. Возвращает `IDebugProperty2` интерфейс из `CFieldProperty` объекта.  
  
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
