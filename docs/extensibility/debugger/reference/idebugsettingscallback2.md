---
title: IDebugSettingsCallback2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2 interface
ms.assetid: 7e525d0b-7d7a-4d1c-8b78-e1398fa922f2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 859522ebdbe231146c73b25c5e4c92fba9809727
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66321944"
---
# <a name="idebugsettingscallback2"></a>IDebugSettingsCallback2
Модули для чтения метрик параметров отладки позволяет удаленно.

## <a name="syntax"></a>Синтаксис

```
IDebugSettingsCallback2D : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
Этот интерфейс реализуется обратным вызовом события диспетчера сеанса отладки и потребляемых отладчиков. Он может также использоваться локально вместо .lib Dbgmetric [d].

## <a name="methods"></a>Методы
В следующей таблице показаны методы `IDebugSettingsCallback2`.

|Метод|Описание|
|------------|-----------------|
|[EnumEEs](../../../extensibility/debugger/reference/idebugsettingscallback2-enumees.md)|Перечисляет вычислители выражений доступны, учитывая идентификаторы языка и поставщика.|
|[GetEELocalObject](../../../extensibility/debugger/reference/idebugsettingscallback2-geteelocalobject.md)|Возвращает локальный объект вычислителя выражения по заданному метрики.|
|[GetEEMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricdword.md)|Извлекает значение, соответствующее заданной метрики средство оценки выражений.|
|[GetEEMetricFile](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricfile.md)|Извлекает метрики файла вычислителя выражений, заданной имя или метрики.|
|[GetEEMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricguid.md)|Извлекает уникальный идентификатор для метрики вычислителя выражения, заданную ее именем.|
|[GetEEMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricstring.md)|Извлекает строковое значение метрики вычислителя выражений, заданную ее именем.|
|[GetMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricdword.md)|Извлекает значение метрики, заданную ее именем.|
|[GetMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricguid.md)|Извлекает уникальный идентификатор метрики с заданным именем.|
|[GetMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricstring.md)|Извлекает строковое значение метрики, заданную ее именем.|

## <a name="requirements"></a>Требования
Заголовок: Msdbg.h

Пространство имен: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Пример
В следующем примере показано функцию, которая принимает **IDebugSettingsCallback2** объект в качестве параметра.

```cpp
HRESULT GetDebugSettingsCallback (IDebugSettingsCallback2 **ppCallback)
{
    HRESULT hRes = E_FAIL;

    if ( ppCallback )
    {
        if ( EVAL(m_pdec) )
            hRes = m_pdec->QueryInterface(IID_IDebugSettingsCallback2, (void **)ppCallback);
        else
            hRes = E_FAIL;
    }
    else
        hRes = E_INVALIDARG;

    return ( hRes );
}
```
