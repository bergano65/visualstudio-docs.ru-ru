---
title: IDebugModule2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2
helpviewer_keywords:
- IDebugModule2 interface
ms.assetid: 24c2a126-f4ab-4891-8509-8ef99b994c08
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a43c7e7ed24da7d73784e20e9e998bdfe69cbd65
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99929757"
---
# <a name="idebugmodule2"></a>IDebugModule2
Этот интерфейс представляет модуль, то есть исполняемый модуль программы, такой как DLL.

## <a name="syntax"></a>Синтаксис

```
IDebugModule2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Модуль отладки (DE) реализует этот интерфейс для представления модуля и предоставления доступа к сведениям об этом модуле.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Вызов метода [module](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md) возвращает этот интерфейс. Метод DE отправляет интерфейс [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) в Диспетчер отладки сеансов (SDM) с помощью метода [event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) .

 Этот интерфейс также может возвращаться в структуре [фрамеинфо](../../../extensibility/debugger/reference/frameinfo.md) (которая возвращается вызовом [енумфрамеинфо](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)).

- [Затем](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md) также возвращает этот интерфейс ([EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) возвращает интерфейс [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md) ).

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugModule2` .

|Метод|Описание|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)|Возвращает [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) , описывающий этот модуль.|
|[ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)|УСТАРЕВШИЕ. НЕ ИСПОЛЬЗУЙТЕ. Перезагружает символы для этого модуля.|

## <a name="remarks"></a>Remarks
 Сведения о модуле можно отобразить в окне **модули** интегрированной среды разработки.

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
- [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)
