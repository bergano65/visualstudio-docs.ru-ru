---
title: IDebugModule2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2
helpviewer_keywords:
- IDebugModule2 interface
ms.assetid: 24c2a126-f4ab-4891-8509-8ef99b994c08
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dbbea1b52133de41dd26f437aeba31a0eff5a50a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726905"
---
# <a name="idebugmodule2"></a>IDebugModule2
Этот интерфейс представляет собой модуль, т.е. исполняемую единицу программы, например DLL.

## <a name="syntax"></a>Синтаксис

```
IDebugModule2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Отладка двигателя (DE) реализует этот интерфейс для представления модуля и обеспечить доступ к информации об этом модуле.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Звонок [в GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md) возвращает этот интерфейс. DE отправляет интерфейс [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) менеджеру отладки сеанса (SDM) с помощью метода [Event.](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)

 Этот интерфейс также может быть возвращен в структуре [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) (которая возвращается по вызову [в EnumFrameInfo).](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)

- [Далее](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md) также возвращает этот интерфейс[(EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) возвращает интерфейс [IEnumDebugModules2).](../../../extensibility/debugger/reference/ienumdebugmodules2.md)

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugModule2`.

|Метод|Описание|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)|Получает [MODULE_INFO,](../../../extensibility/debugger/reference/module-info.md) описывающий этот модуль.|
|[ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)|Устаревшее. НЕ ИСПОЛЬЗУЙТЕ. Перезагружает символы для этого модуля.|

## <a name="remarks"></a>Примечания
 Информация о модуле может отображаться в окне **модулей** IDE.

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
- [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)
