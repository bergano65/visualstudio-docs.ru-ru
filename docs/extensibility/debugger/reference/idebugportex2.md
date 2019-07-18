---
title: IDebugPortEx2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2
helpviewer_keywords:
- IDebugPortEx2 interface
ms.assetid: 144724d0-38ee-4c9b-87ca-8a504371182b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bed6cd047af4ba57a1880d87e30a990dcf83efac
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340435"
---
# <a name="idebugportex2"></a>IDebugPortEx2
Этот интерфейс позволяет сеанс отладки управление manager (SDM), программы и процессы, запущенные на порт.

## <a name="syntax"></a>Синтаксис

```
IDebugPortEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Пользовательский порт поставщик реализует этот интерфейс на тот же объект, реализующий [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md).

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 Вызовы SDM [QueryInterface](/cpp/atl/queryinterface) на `IDebugPort2` интерфейс для получения этого интерфейса.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugPortEx2`.

|Метод|Описание|
|------------|-----------------|
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)|Запускает исполняемый файл.|
|[ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)|Возобновляет выполнение процесса.|
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugportex2-canterminateprocess.md)|Определяет, можно ли завершить процесс.|
|[TerminateProcess](../../../extensibility/debugger/reference/idebugportex2-terminateprocess.md)|Завершает процесс.|
|[GetPortProcessId](../../../extensibility/debugger/reference/idebugportex2-getportprocessid.md)|Получает идентификатор процесса сам класс port.|
|[GetProgram](../../../extensibility/debugger/reference/idebugportex2-getprogram.md)|Возвращает программу, сопоставленную с узлом программы.|

## <a name="remarks"></a>Примечания
 Этот интерфейс обычно закрыт между SDM и поставщика пользовательского порта.

 При желании модуля отладки (DE) можно найти на этом интерфейсе [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) передается интерфейс [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) и использовать [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) для запуска программы. Это не является обязательным, но DE можно сделать то, что нужно сделать, чтобы запустить программу запроса.

## <a name="requirements"></a>Требования
 Заголовок: portpriv.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)