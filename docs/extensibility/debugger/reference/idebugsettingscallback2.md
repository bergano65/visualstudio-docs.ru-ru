---
title: IDebugSettingsCallback2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2 interface
ms.assetid: 7e525d0b-7d7a-4d1c-8b78-e1398fa922f2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2c85b54f92970dca5d712b827019300f850b03cc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719939"
---
# <a name="idebugsettingscallback2"></a>IDebugSettingsCallback2
Позволяет отладить двигатели для чтения параметров метрики удаленно.

## <a name="syntax"></a>Синтаксис

```
IDebugSettingsCallback2D : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
Этот интерфейс реализован путем обратного вызова сеанса отладки и потребляется отладоть двигатели. Он также может быть использован на местном уровне, а не Dbgmetric.d.lib.

## <a name="methods"></a>Методы
В следующей таблице показаны методы `IDebugSettingsCallback2`.

|Метод|Описание|
|------------|-----------------|
|[EnumEEs](../../../extensibility/debugger/reference/idebugsettingscallback2-enumees.md)|Перечисляет доступные оценщики выражений с учетом идентификаторов языка и поставщиков.|
|[GetEELocalObject](../../../extensibility/debugger/reference/idebugsettingscallback2-geteelocalobject.md)|Извлекает локальный объект оценщика выражения с учетом метрики.|
|[GetEEMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricdword.md)|Извлекает значение, которое соответствует указанной метрике оценщика выражения.|
|[GetEEMetricFile](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricfile.md)|Извлекает файл метрики оценщика выражения с учетом имени или метрики.|
|[GetEEMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricguid.md)|Извлекает уникальный идентификатор для метрики оценки выражения, учитывая его имя.|
|[GetEEMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricstring.md)|Извлекает строку значения метрики оценки выражения с учетом его имени.|
|[GetMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricdword.md)|Получает значение метрики, учитывая ее имя.|
|[GetMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricguid.md)|Извлекает уникальный идентификатор метрики, учитывая его имя.|
|[GetMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricstring.md)|Извлекает строку значения метрики с учетом ее имени.|

## <a name="requirements"></a>Требования
Заголовок: Msdbg.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Пример
В следующем примере показана функция, которая использует объект **IDebugSettingsCallback2** в качестве параметра.

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
