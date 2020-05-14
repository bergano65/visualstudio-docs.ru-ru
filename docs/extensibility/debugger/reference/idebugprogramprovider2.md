---
title: IDebugProgramProvider2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2
helpviewer_keywords:
- IDebugProgramProvider2 interface
ms.assetid: a9ec7b3e-a59c-4069-b2ee-6f45916eeb78
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 43557e5d81e5140967a1189e57a350595d0f7220
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721692"
---
# <a name="idebugprogramprovider2"></a>IDebugProgramProvider2
Этот зарегистрированный интерфейс позволяет диспетчеру отладки сеанса (SDM) получать информацию о программах, которые были "опубликованы" через интерфейс [IDebugProgramPublisher2.](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)

## <a name="syntax"></a>Синтаксис

```
IDebugProgramProvider2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
Движок отладки (DE) реализует этот интерфейс, чтобы предоставить информацию о отладке программ. Этот интерфейс зарегистрирован в разделе DE реестра `metricProgramProvider`с использованием метрики, как описано в [SDK Helpers для отладки.](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)

## <a name="notes-for-callers"></a>Заметки для абонентов
Позвоните `CoCreateInstance` `CLSID` функции COM с поставщиком программы, который получен из реестра. Смотрите пример.

## <a name="methods-in-vtable-order"></a>Методы в порядке Vtable

|Метод|Описание|
|------------|-----------------|
|[GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)|Получает информацию о запущенных программах, отфильтрованных различными способами.|
|[GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)|Получает узл программы, учитывая определенный идентификатор процесса.|
|[WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)|Устанавливает обратный вызов для просмотра событий поставщика, связанных с определенными видами процессов.|
|[Setlocale](../../../extensibility/debugger/reference/idebugprogramprovider2-setlocale.md)|Устанавливает язык для любых языковых ресурсов, необходимых DE.|

## <a name="remarks"></a>Примечания
Как правило, процесс использует этот интерфейс, чтобы узнать о программах, работающих в этом процессе.

## <a name="requirements"></a>Требования
Заголовок: msdbg.h

Название: Microsoft.VisualStudio.Debugger.Interop

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
