---
title: IDebugProgramProvider2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2
helpviewer_keywords:
- IDebugProgramProvider2 interface
ms.assetid: a9ec7b3e-a59c-4069-b2ee-6f45916eeb78
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6f392e823d28440a73a1aaa606351c28c6e9c70
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66343358"
---
# <a name="idebugprogramprovider2"></a>IDebugProgramProvider2
Зарегистрированные, этот интерфейс позволяет сеанса отладки manager (SDM) для получения сведений о программах, которые были «опубликованы» через [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md) интерфейс.

## <a name="syntax"></a>Синтаксис

```
IDebugProgramProvider2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
Модуль отладки (DE) реализует этот интерфейс для предоставления сведений о отлаживаемых программ. Этот интерфейс зарегистрирован в разделе реестра, с помощью метрики DE `metricProgramProvider`, как описано в разделе [вспомогательные пакеты SDK для отладки](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
Вызов COM `CoCreateInstance` функционировать с `CLSID` поставщика программы, полученный из реестра. См. пример.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable

|Метод|Описание|
|------------|-----------------|
|[GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)|Получает сведения о программах под управлением, фильтруются в различными способами.|
|[GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)|Возвращает узел программы, получив идентификатор определенного процесса.|
|[WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)|Задает обратный вызов для отслеживания для поставщика событий, связанных с определенными типами процессов.|
|[SetLocale](../../../extensibility/debugger/reference/idebugprogramprovider2-setlocale.md)|Устанавливает языковой стандарт для любого конкретного языка, необходимую для DE.|

## <a name="remarks"></a>Примечания
Как правило процесс использует этот интерфейс, чтобы узнать о программ, работающих в этом процессе.

## <a name="requirements"></a>Требования
Header: msdbg.h

Пространство имен: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Пример

```cpp
IDebugProgramProvider2 *GetProgramProvider(GUID *pDebugEngineGuid)
{
    // This is typically defined globally. For this example, it is
    // defined here.
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";
    IDebugProgramProvider2 *pProvider = NULL;
    if (pDebugEngineGuid != NULL) {
        CLSID clsidProvider = { 0 };
        ::GetMetric(NULL,
                    metrictypeEngine,
                    *pDebugEngineGuid,
                    metricProgramProvider,
                    &clsidProvider,
                    strRegistrationRoot);
        if (!IsEqualGUID(clsidProvider,GUID_NULL)) {
            CComPtr<IDebugProgramProvider2> spProgramProvider;
            spProgramProvider.CoCreateInstance(clsidProvider);
            if (spProgramProvider != NULL) {
                pProvider = spProgramProvider.Detach();
            }
        }
    }
    return(pProvider);
}
```

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [Вспомогательные пакеты SDK для отладки](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
