---
title: IEnumDebugFrameInfo2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFrameInfo2
helpviewer_keywords:
- IEnumDebugFrameInfo2
ms.assetid: 994e30ad-435a-4f9e-9272-d96d9e01099c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6579481f44006cc3f77e57a9c9ecbd327c3b7409
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350283"
---
# <a name="ienumdebugframeinfo2"></a>IEnumDebugFrameInfo2
Этот интерфейс перечисляет [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) структуры.

## <a name="syntax"></a>Синтаксис

```
IEnumDebugFrameInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Модуль отладки (DE) реализует этот интерфейс, чтобы предоставить список структур, описывающий текущий стек вызовов.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 Visual Studio вызывает [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) для получения этого интерфейса, каждый раз, когда точки останова, исключение, или остановка происходит в отлаживаемой программы.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IEnumDebugFrameInfo2`.

|Метод|Описание|
|------------|-----------------|
|[Вперед](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)|Извлекает указанное число [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) структур в последовательности перечисления.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugframeinfo2-skip.md)|Пропускает заданное число [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) структур в последовательности перечисления.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugframeinfo2-reset.md)|Сбрасывает последовательность перечислений в начало.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugframeinfo2-clone.md)|Создает перечислитель с тем же состоянием перечисления, что и текущий перечислитель.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)|Получает число [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) структур в перечислителе.|

## <a name="remarks"></a>Примечания
 Visual Studio получает этот интерфейс в качестве первого шага к обработке точки останова, исключений или пользовательские Пауза вкл отлаживаемой программы. Список [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) структуры представляет текущий стек вызовов, с текущим вызовом функции в начале списка и самая старая функция, вызовите в конце списка. Каждый `FRAMEINFO` представляет кадр стека, контекст, в котором выражения и посмотрели локальных переменных.

## <a name="requirements"></a>Требования
 Header: msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)