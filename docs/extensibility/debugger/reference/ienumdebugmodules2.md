---
title: IEnumDebugModules2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugModules2
helpviewer_keywords:
- IEnumDebugModules2
ms.assetid: 4fe28074-a960-41ad-b74d-b57f04c0c0ad
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 548bcd0328f7bdf52e47eb9a4295168ca47a2517
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2019
ms.locfileid: "65226699"
---
# <a name="ienumdebugmodules2"></a>IEnumDebugModules2
Этот интерфейс перечисляет список модулей.

## <a name="syntax"></a>Синтаксис

```
IEnumDebugModules2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Модуль отладки (DE) реализует этот интерфейс для представления списка модулей, загруженных для программы.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 Visual Studio вызывает [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) для получения этого интерфейса.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IEnumDebugModules2`.

|Метод|Описание|
|------------|-----------------|
|[Вперед](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md)|Извлекает указанное число модулей в последовательности перечисления.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugmodules2-skip.md)|Пропускает указанное число модулей в последовательности перечисления.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugmodules2-reset.md)|Сбрасывает последовательность перечислений в начало.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugmodules2-clone.md)|Создает перечислитель с тем же состоянием перечисления, что и текущий перечислитель.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugmodules2-getcount.md)|Возвращает число модулей.|

## <a name="remarks"></a>Примечания
 Visual Studio использует этот интерфейс в основном для того, чтобы обновить **модули** окна.

 В целях отладки в Visual Studio, программа находится в логической последовательности инструкций кода, которые может пересекать границы модуля, поэтому потребность в список модулей для одного [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) интерфейс. Первый модуль в списке обычно содержит начальной отправной точкой для соответствующую программу.

## <a name="requirements"></a>Требования
 Header: msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)