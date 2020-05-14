---
title: IDebugEngineLaunch2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2
helpviewer_keywords:
- IDebugEngineLaunch2 interface
ms.assetid: 5eaf2ad8-3fbf-446e-b48b-5327ad3f5255
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ee77cbd680df2c851d53aac298605023227fa6f8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730492"
---
# <a name="idebugenginelaunch2"></a>IDebugEngineLaunch2
Используется движком отладки (DE) для запуска и прекращения программ.

## <a name="syntax"></a>Синтаксис

```
IDebugEngineLaunch2 : IDebugEngine2
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Этот интерфейс реализован пользовательским DE, если он имеет особые требования для запуска процесса, который не может быть полностью обработан пользовательским портом. Обычно это происходит в случае, когда DE является частью устного переводчика, а процесс отладки — это сценарий: сначала необходимо запустить переводчика, а затем загрузить и запустить скрипт. Порт может запустить переводчика, но скрипт может потребовать специальной обработки (где DE имеет роль). Этот интерфейс реализован только при наличии уникальных требований к запуску программы, с помощью которого пользовательский порт не может справиться.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Этот интерфейс вызывается менеджером отладки сеанса (SDM), если SDM может получить этот интерфейс из интерфейса [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) (с помощью queryInterface). Если этот интерфейс может быть получен, SDM знает, что DE имеет особые требования и призывает этот интерфейс для запуска программы вместо того, чтобы порт запустить его.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugEngineLaunch2`.

|Метод|Описание|
|------------|-----------------|
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)|Запускает процесс с помощью DE.|
|[ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)|Возобновляет выполнение процесса.|
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md)|Определяет, может ли процесс быть прекращен.|
|[TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)|Прекращает процесс.|

## <a name="requirements"></a>Требования
 Заголовок: Msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
