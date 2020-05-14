---
title: IEnumDebugОшибкаОшибок2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugErrorBreakpoints2
helpviewer_keywords:
- IEnumDebugErrorBreakpoints2
ms.assetid: ffdad73d-969a-45ef-9ad1-7f5d3b814018
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ea841a095964b71e301e966bfd0a10c8f7c0c65d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716883"
---
# <a name="ienumdebugerrorbreakpoints2"></a>IEnumDebugErrorBreakpoints2
Этот интерфейс перечисляет точки разрыва ошибок, связанные с ожидавшейся точкой разрыва.

## <a name="syntax"></a>Синтаксис

```
IEnumDebugErrorBreakpoints2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Движок отладки (DE) реализует этот интерфейс как часть своей поддержки точек разрыва.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Visual Studio вызывает [CanBind,](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) чтобы получить этот интерфейс, представляющий список моментов разрыва, которые не могут быть связаны, или [EnumErrorBreakpoints,](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md) чтобы получить этот интерфейс, представляющий список точек разрыва, которые не были связаны.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IEnumDebugErrorBreakpoints2`.

|Метод|Описание|
|------------|-----------------|
|[Далее](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-next.md)|Извлекает определенное количество моментов ошибки в последовательности перечисления.|
|[Пропустить](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-skip.md)|Пропускает определенное количество моментов ошибки в последовательности перечисления.|
|[Сбросить](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-reset.md)|Сбрасывает последовательность перечислений в начало.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-clone.md) (Клонировать)|Создает регистратор, содержащий то же состояние перечисления, что и текущий регистратор.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-getcount.md)|Получает количество моментов ошибки в регистраторе.|

## <a name="remarks"></a>Примечания
 Этот интерфейс содержит список интерфейсов [IDebugErrorBreakpoint2,](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) каждый из которых описывает точку разрыва, которая не может быть связана и почему она не может быть связана. Visual Studio `IEnumDebugErrorBreakpoint2` использует интерфейс для обновления моментов, показанных в IDE.

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)
- [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
