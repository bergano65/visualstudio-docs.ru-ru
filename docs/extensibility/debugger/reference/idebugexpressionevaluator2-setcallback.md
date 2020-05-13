---
title: IDebugExpressionОценка2::SetCallback (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::SetCallback
- SetCallback
ms.assetid: 31e3a99e-e784-44a3-8b19-cc5ef31ed546
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 907fdaa928b3f84f6ff37490d5c54a9d48515053
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729345"
---
# <a name="idebugexpressionevaluator2setcallback"></a>IDebugExpressionEvaluator2::SetCallback
Позволяет оценщику выражения (EE) указать интерфейс обратного вызова, который будет использовать движок отладчика (DE) для чтения параметров метрики.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetCallback (
    IDebugSettingsCallback2* pCallback
);
```

```csharp
int SetCallback (
    IDebugSettingsCallback2 pCallback
);
```

## <a name="parameters"></a>Параметры
`pCallback`\
(в) Интерфейс для использования для настроек обратного вызова.

## <a name="return-value"></a>Возвращаемое значение
Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
Этот метод предоставляет интерфейс менеджеру отладки сеанса, который оценщик выражения может использовать для чтения параметров метрики. Это полезно при удаленной отладке [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] для чтения метрик на компьютере.

## <a name="example"></a>Пример
Ниже приведены следующие примеры, как реализовать этот метод для объекта **ЦВЕ,** который предоставляет интерфейс [IDebugSettingsCallback2.](../../../extensibility/debugger/reference/idebugsettingscallback2.md)

```cpp
HRESULT CEE::SetCallback(IDebugSettingsCallback2* in_pCallback)
{
    // precondition
    INVARIANT( this );

    // function body
    if (NULL != this->m_LanguageSpecificUseCases.pfSetCallback)
    {
        EEDomain::fSetCallback DomainVal =
        {
            in_pCallback
        };

        BOOL bSuccess = (*this->m_LanguageSpecificUseCases.pfSetCallback)(DomainVal);
        ENSURE( bSuccess );
    }

    // postcondition
    INVARIANT( this );

    return S_OK;
}
```

## <a name="see-also"></a>См. также
- [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
