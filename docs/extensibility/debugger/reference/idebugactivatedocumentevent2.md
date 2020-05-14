---
title: IDebugАктивированоДокументальныйТурнир2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugActivateDocumentEvent2
helpviewer_keywords:
- IDebugActivateDocumentEvent2 interface
ms.assetid: 6f37edd7-a48c-4b41-b160-dff9be63a284
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f601027ce9e71dff6687bcd6aa1b08f13f5ce0cf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736614"
---
# <a name="idebugactivatedocumentevent2"></a>IDebugActivateDocumentEvent2
Движок отладки (DE) использует этот интерфейс для запроса документа для загрузки.

## <a name="syntax"></a>Синтаксис

```
IDebugActivateDocumentEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 DE реализует этот интерфейс, когда ему требуется исходный файл для открытия. Этот интерфейс реализован только путем отладки двигателей, которые работают с или являются частью скриптов переводчиков. Интерфейс [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) должен быть реализован на том же объекте, что и этот `IDebugEvent2` интерфейс (SDM использует [queryInterface](/cpp/atl/queryinterface) для доступа к интерфейсу).

## <a name="notes-for-callers"></a>Заметки для абонентов
 DE создает и отправляет объект события, когда ему необходимо открыть исходный файл. Событие отправляется с помощью функции обратного вызова [IDebugEventCallback2,](../../../extensibility/debugger/reference/idebugeventcallback2.md) поставляемой SDM при его подключении к отладке программы.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugActivateDocumentEvent2`.

|Методы|Описание|
|-------------|-----------------|
|[GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)|Получает документ для активации.|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)|Получает контекст документа, описывающий позицию в документе.|

## <a name="remarks"></a>Примечания
 Типичный сценарий, в котором этот интерфейс используется, если ошибка разбора происходит в коде скрипта на странице HTML, скрипт DE отправляет этот интерфейс в SDM, так что документ с ошибкой разбора может быть отображается.

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
