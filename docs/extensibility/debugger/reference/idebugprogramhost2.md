---
title: IDebugProgramHost2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramHost2
helpviewer_keywords:
- IDebugProgramHost2 interface
ms.assetid: 2c37b3aa-97a9-4665-8709-edd917f18cb1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 64db456e0c438f8665f122c3cd1b079c2ad1cea1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722213"
---
# <a name="idebugprogramhost2"></a>IDebugProgramHost2
Этот интерфейс предоставляет хост (процесс) информацию о программе.

## <a name="syntax"></a>Синтаксис

```
IDebugProgramHost2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Отладка движок реализует этот интерфейс на том же объекте, что и интерфейс [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) для предоставления информации о процессе хостинга. Это дополнительный интерфейс.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Вызов [queryInterface](/cpp/atl/queryinterface) `IDebugProgram2` на интерфейс, чтобы получить этот интерфейс.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugProgramHost2`.

|Метод|Описание|
|------------|-----------------|
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramhost2-gethostname.md)|Получает название, дружеское имя или название файла процесса хостинга этой программы.|
|[GetHostId](../../../extensibility/debugger/reference/idebugprogramhost2-gethostid.md)|Получает идентификатор процесса хостинга этой программы.|
|[GetHostMachineName](../../../extensibility/debugger/reference/idebugprogramhost2-gethostmachinename.md)|Получает название машины, на которой работает процесс хостинга этой программы.|

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
