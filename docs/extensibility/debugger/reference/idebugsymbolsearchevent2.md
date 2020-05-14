---
title: IDebugСимволПоискВент2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolSearchEvent2
helpviewer_keywords:
- IDebugSymbolSearchEvent2
ms.assetid: 9b946d55-ff85-44eb-b40a-efbf8282eafd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cbe99422e506fb86b0a7e1d9d3242783f3258e6a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718783"
---
# <a name="idebugsymbolsearchevent2"></a>IDebugSymbolSearchEvent2
Этот интерфейс отправляется движком отладки (DE) для указания на то, что символы отладки модуля были загружены.

## <a name="syntax"></a>Синтаксис

```
IDebugSymbolSearchEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 DE реализует этот интерфейс, чтобы сообщить, что символы модуля были загружены. Интерфейс [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) должен быть реализован на том же объекте, что и этот интерфейс. SDM использует [QueryInterface](/cpp/atl/queryinterface) для `IDebugEvent2` доступа к интерфейсу.

## <a name="notes-for-callers"></a>Заметки для абонентов
 DE создает и отправляет объект события, чтобы сообщить, что символы модуля были загружены. Событие отправляется с помощью функции обратного вызова [IDebugEventCallback2,](../../../extensibility/debugger/reference/idebugeventcallback2.md) которая поставляется SDM при подключении к отладке программы.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 Интерфейс `IDebugSymbolSearchEvent2` предоставляет следующий метод.

|Метод|Описание|
|------------|-----------------|
|[GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)|Извлекает информацию о результатах поиска символов.|

## <a name="remarks"></a>Примечания
 Это событие будет отправлено, даже если символы не загрузили. Вызов `IDebugSymbolSearchEvent2::GetSymbolSearchInfo` позволяет обработчику этого события определить, действительно ли модуль имеет какие-либо символы.

 Visual Studio обычно использует это событие для обновления состояния загруженных символов в окне **модулей.**

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
