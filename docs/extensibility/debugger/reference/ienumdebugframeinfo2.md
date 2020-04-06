---
title: IEnumDebugFrameInfo2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFrameInfo2
helpviewer_keywords:
- IEnumDebugFrameInfo2
ms.assetid: 994e30ad-435a-4f9e-9272-d96d9e01099c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0aa67792ced94afd9c4439cbc6ea577e6b85f28b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716606"
---
# <a name="ienumdebugframeinfo2"></a>IEnumDebugFrameInfo2
Этот интерфейс перечисляет структуры [FRAMEINFO.](../../../extensibility/debugger/reference/frameinfo.md)

## <a name="syntax"></a>Синтаксис

```
IEnumDebugFrameInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Движок отладки (DE) реализует этот интерфейс, чтобы предоставить список структур, описывающий текущий стек вызовов.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Visual Studio вызывает [EnumFrameInfo,](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) чтобы получить этот интерфейс всякий раз, когда происходит точка разрыва, исключение или остановка в отладке программы.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IEnumDebugFrameInfo2`.

|Метод|Описание|
|------------|-----------------|
|[Далее](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)|Извлекает определенное количество структур [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) в последовательности перечисления.|
|[Пропустить](../../../extensibility/debugger/reference/ienumdebugframeinfo2-skip.md)|Пропускает определенное количество структур [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) в последовательности перечисления.|
|[Сбросить](../../../extensibility/debugger/reference/ienumdebugframeinfo2-reset.md)|Сбрасывает последовательность перечислений в начало.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugframeinfo2-clone.md) (Клонировать)|Создает регистратор, содержащий то же состояние перечисления, что и текущий регистратор.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)|Получает количество структур [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) в регистраторе.|

## <a name="remarks"></a>Примечания
 Visual Studio получает этот интерфейс в качестве первого шага к обработке точки разрыва, исключения или пользовательской паузы на отладке программы. Список структур [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) представляет текущий стек вызовов с текущим вызовом функции в начале списка и самым старым вызовом функции в конце списка. Каждый из них `FRAMEINFO` представляет кадр стека, контекст, в котором можно оценивать выражения и рассматривать локальные переменные.

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
