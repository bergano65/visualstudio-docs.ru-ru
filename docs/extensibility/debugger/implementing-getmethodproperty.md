---
title: Реализация Жетмесодпроперти | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetMethodProperty method
- IDebugExpressionEvaluator2 property
ms.assetid: 6305874f-a2c4-4432-834c-07530ea84bff
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 252d09eee9c69ca75cb46d28dde807f2c500737f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738518"
---
# <a name="implement-getmethodproperty"></a>Реализация Жетмесодпроперти
> [!IMPORTANT]
> В Visual Studio 2015 такой способ реализации оценивающих выражений является устаревшим. Дополнительные сведения о реализации вычислителей выражений CLR см. в разделе средства [оценки выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [Пример управляемого средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

Visual Studio вызывает [жетдебугпроперти](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)отладчика (de), который, в свою очередь, вызывает [жетмесодпроперти](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) для получения сведений о текущем методе в кадре стека.

Эта реализация `IDebugExpressionEvaluator::GetMethodProperty` выполняет следующие задачи:

1. Вызывает [жетконтаинерфиелд](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md), передавая объект [идебугаддресс](../../extensibility/debugger/reference/idebugaddress.md) . Поставщик символов (SP) возвращает [идебугконтаинерфиелд](../../extensibility/debugger/reference/idebugcontainerfield.md) , представляющий метод, который содержит указанный адрес.

2. Получает [идебугмесодфиелд](../../extensibility/debugger/reference/idebugmethodfield.md) из `IDebugContainerField` .

3. Создает экземпляр класса (вызываемого `CFieldProperty` в этом примере), который реализует интерфейс [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) и содержит `IDebugMethodField` объект, возвращенный из SP.

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

## <a name="see-also"></a>См. также раздел
- [Пример реализации локальных переменных](../../extensibility/debugger/sample-implementation-of-locals.md)
