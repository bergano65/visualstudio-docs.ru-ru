---
title: IDebugOutputStringEvent2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugOutputStringEvent2
helpviewer_keywords:
- IDebugOutputStringEvent2 interface
ms.assetid: 86596fd1-cecc-4813-8add-dc3d70068f9b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dfce52f89e75c8e9e697a3fa5ad4184c3d1fa42b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62872516"
---
# <a name="idebugoutputstringevent2"></a>IDebugOutputStringEvent2
Этот интерфейс отправляется ядром отладки (DE) диспетчер отладки сеансов (SDM) для вывода строки.

## <a name="syntax"></a>Синтаксис

```
IDebugOutputStringEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 DE реализует этот интерфейс для отправки строки в **вывода** окно интегрированной среды разработки. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) интерфейс должен быть реализован на один и тот же объект как следующий интерфейс. Использует SDM [QueryInterface](/cpp/atl/queryinterface) для доступа к `IDebugEvent2` интерфейс.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 DE создает и отправляет этот объект события отправки строки в **вывода** окна. Это событие отправляется с помощью [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) функцию обратного вызова, предоставляемую SDM, когда он присоединен к отлаживаемой программы.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны метод `IDebugOutputStringEvent2`.

|Метод|Описание|
|------------|-----------------|
|[GetString](../../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md)|Получает отображаемое сообщение.|

## <a name="remarks"></a>Примечания
 Например, в неуправляемом коде, строку, чтобы ее выходные данные могут быть получены при отлаживаемой программы отправляет строку в Win32 `OutputDebugString` функции. Такая строка перехвачен DE и отправляемые SDM как `IDebugOutputStringEvent2` событий.

 Используйте [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md) отправлять сообщение, которое требует ответ от пользователя.

 Используйте [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) для отправки сообщения об ошибке, требующее ответа.

## <a name="requirements"></a>Требования
 Header: msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)