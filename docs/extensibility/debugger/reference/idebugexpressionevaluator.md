---
title: IDebugЭкспрессумодор (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator
helpviewer_keywords:
- IDebugExpressionEvaluator interface
ms.assetid: 0636d8c3-625a-49fa-94b6-516f22b7e1bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e8dd910e4edc110abb40dde14b4cb85ff54a70a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729383"
---
# <a name="idebugexpressionevaluator"></a>IDebugExpressionEvaluator
> [!IMPORTANT]
> В Visual Studio 2015 этот способ внедрения оценщиков экспресс-выражений унижается. Для получения информации о реализации оценщиков экспрессии CLR, пожалуйста, ознакомьтесь с [clR Expression Evaluators](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [образцом управляемого оценщика экспрессии.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

Этот интерфейс представляет собой оценщика выражения.

## <a name="syntax"></a>Синтаксис

```
IDebugExpressionEvaluator : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
Оценщик выражения должен реализовать этот интерфейс.

## <a name="notes-for-callers"></a>Заметки для абонентов
Чтобы получить этот интерфейс, мгновенноо оценивающего выражения с помощью `CoCreateInstance` метода с помощью идентификатора класса (CLSID) оценщика. Смотрите пример.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
В следующей таблице показаны методы `IDebugExpressionEvaluator`.

|Метод|Описание|
|------------|-----------------|
|[Синтаксический анализ](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)|Преобразует строку выражения в разогнанное выражение.|
|[GetMethodProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)|Получает локальные переменные, аргументы и другие свойства метода.|
|[GetMethodLocationProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodlocationproperty.md)|Преобразует местоположение метода и смещение в адрес памяти.|
|[Setlocale](../../../extensibility/debugger/reference/idebugexpressionevaluator-setlocale.md)|Определяет, какой язык использовать для создания результатов печати.|
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugexpressionevaluator-setregistryroot.md)|Устанавливает корень реестра. Используется для боковой отладки.|

## <a name="remarks"></a>Примечания
В типичной ситуации, отладка двигателя (DE) мгновенно выражение оценщика (EE) в результате вызова [parseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md). Поскольку DE знает язык и поставщика EE, который он хочет использовать, DE получает CLSID EE из реестра (функция `GetEEMetric` [SDK Helpers для отладки,](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) , помогает с этим поиском).

После мгновенного EE DE вызывает [Parse,](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) чтобы разобрать выражение и хранить его в объекте [IDebugParsedExpression.](../../../extensibility/debugger/reference/idebugparsedexpression.md) Позже, вызов [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) оценивает выражение.

## <a name="requirements"></a>Требования
Заголовок: ee.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Пример
В этом примере показано, как мгновенно оценить выражение, учитывая поставщика символов и адрес в исходном коде. Этот пример использует `GetEEMetric`функцию, от [SDK Помощники для библиотеки debugging,](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) dbgmetric.lib.

```cpp
IDebugExpressionEvaluator GetExpressionEvaluator(IDebugSymbolProvider pSymbolProvider,
                                                 IDebugAddress *pSourceAddress)
{
    // This is typically defined globally but is specified here just
    // for this example.
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";

    IDebugExpressionEvaluator *pEE = NULL;
    if (pSymbolProvider != NULL && pSourceAddress != NULL) {
        HRESULT hr         = S_OK;
        GUID  languageGuid = { 0 };
        GUID  vendorGuid   = { 0 };

        hr = pSymbolProvider->GetLanguage(pSourceAddress,
                                          &languageGuid,
                                          &vendorGuid);
        if (SUCCEEDED(hr)) {
            CLSID clsidEE = { 0 };
            CComPtr<IDebugExpressionEvaluator> spExpressionEvaluator;
            // Get the expression evaluator's CLSID from the registry.
            ::GetEEMetric(languageGuid,
                          vendorGuid,
                          metricCLSID,
                          &clsidEE,
                          strRegistrationRoot);
            if (!IsEqualGUID(clsidEE,GUID_NULL)) {
                // Instantiate the expression evaluator.
                spExpressionEvaluator.CoCreateInstance(clsidEE);
            }
            if (spExpressionEvaluator != NULL) {
                pEE = spExpressionEvaluator.Detach();
            }
        }
    }
    return pEE;
}
```

## <a name="see-also"></a>См. также
- [Интерфейсы вычисления выражений](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)
- [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [Вспомогательные пакеты SDK для отладки](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
