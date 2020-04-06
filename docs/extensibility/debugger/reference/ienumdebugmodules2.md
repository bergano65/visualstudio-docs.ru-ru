---
title: IEnumDebugModules2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugModules2
helpviewer_keywords:
- IEnumDebugModules2
ms.assetid: 4fe28074-a960-41ad-b74d-b57f04c0c0ad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 612285aa4d5a249c0f922ccae88d98a7df83187b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716445"
---
# <a name="ienumdebugmodules2"></a>IEnumDebugModules2
Этот интерфейс перечисляет список модулей.

## <a name="syntax"></a>Синтаксис

```
IEnumDebugModules2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Движок отладки (DE) реализует этот интерфейс, чтобы представить список модулей, загруженных для программы.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Visual Studio вызывает [EnumModules,](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) чтобы получить этот интерфейс.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IEnumDebugModules2`.

|Метод|Описание|
|------------|-----------------|
|[Далее](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md)|Извлекает определенное количество модулей в последовательности перечисления.|
|[Пропустить](../../../extensibility/debugger/reference/ienumdebugmodules2-skip.md)|Пропускает определенное количество модулей в последовательности перечисления.|
|[Сбросить](../../../extensibility/debugger/reference/ienumdebugmodules2-reset.md)|Сбрасывает последовательность перечислений в начало.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugmodules2-clone.md) (Клонировать)|Создает регистратор, содержащий то же состояние перечисления, что и текущий регистратор.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugmodules2-getcount.md)|Получает количество модулей.|

## <a name="remarks"></a>Примечания
 Visual Studio использует этот интерфейс в первую очередь для обновления окна **модулей.**

 Для отладки в Visual Studio программа представляет собой логическую последовательность инструкций по коду, которая может пересекать границы модулей, отсюда и необходимость в списке модулей для одного интерфейса [IDebugProgram2.](../../../extensibility/debugger/reference/idebugprogram2.md) Первый модуль в списке обычно содержит начальную точку входа для сопутствуной программы.

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)
