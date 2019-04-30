---
title: IDebugPortEx2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2
helpviewer_keywords:
- IDebugPortEx2 interface
ms.assetid: 144724d0-38ee-4c9b-87ca-8a504371182b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 392b922eb8312906713ba7b5808ed117e20277b5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62871794"
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