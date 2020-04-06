---
title: IDebugModule3 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3
helpviewer_keywords:
- IDebugModule3 interface
ms.assetid: 44f8e96e-9c59-4ffc-9a08-9c908a0e4de7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 84db1b672a9460ef3809162a2a1433f269796046
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726743"
---
# <a name="idebugmodule3"></a>IDebugModule3
Этот интерфейс представляет собой модуль, поддерживающий альтернативные местоположения символов и состояния JustMyCode.

## <a name="syntax"></a>Синтаксис

```
IDebugModule3 : IDebugModule2
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Отладка двигателя (DE) реализует этот интерфейс для поддержки альтернативных местоположений символов и для работы с JustMyCode государств (см. [Visual Studio Debugger Glossary](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md) для определения "JustMyCode").

## <a name="notes-for-callers"></a>Заметки для абонентов
 Звонок в [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md) возвращает этот интерфейс. DE отправляет интерфейс [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) менеджеру отладки сеанса (SDM) с помощью метода [Event.](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) Кроме того, звонок [в QueryInterface](/cpp/atl/queryinterface) на интерфейсе [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) возвращает этот интерфейс.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В дополнение к методам на интерфейсе [IDebugModule2,](../../../extensibility/debugger/reference/idebugmodule2.md) этот интерфейс реализует следующие методы:

|Метод|Описание|
|------------|-----------------|
|[GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)|Возвращает список путей, иснаемых для символов, и результаты поиска каждого пути.|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)|Загружает и инициализирует символы для текущего модуля.|
|[IsUserCode](../../../extensibility/debugger/reference/idebugmodule3-isusercode.md)|Возвращает флаг с указанием того, представляет ли модуль код пользователя.|
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugmodule3-setjustmycodestate.md)|Уточняется, следует ли считать модуль кодом пользователя или нет.|

## <a name="remarks"></a>Примечания
 Visual Studio является типичным потребителем этого интерфейса.

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)
- [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)
