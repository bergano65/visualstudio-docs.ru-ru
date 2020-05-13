---
title: IDebugProcessEx2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2
helpviewer_keywords:
- IDebugProcessEx2 interface
ms.assetid: 44e309ba-1d6f-499b-aa7e-9b34858a6d57
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 743dd1aa72d9b8db6b848618c8a2ad6c8c8ecaaf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723337"
---
# <a name="idebugprocessex2"></a>IDebugProcessEx2
Этот интерфейс позволяет диспетчеру отладки сеанса (SDM) уведомлять процесс, к который он прикрепляется или отделяется от процесса.

## <a name="syntax"></a>Синтаксис

```
IDebugProcessEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Поставщик пользовательских портов реализует этот интерфейс на том же объекте, что и интерфейс [IDebugProcess2,](../../../extensibility/debugger/reference/idebugprocess2.md) чтобы:

- Отслеживание сеансов поддержки, подключенных к процессу

- Поддержка автоматического присоединения через несколько двигателей отладки

  Поставщик пользовательских портов может реализовать этот интерфейс, если он выбирает.

## <a name="notes-for-callers"></a>Заметки для абонентов

- SDM вызывает [queryInterface](/cpp/atl/queryinterface) `IDebugProcess2` на интерфейсе для того чтобы получить этот интерфейс.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugProcessEx2`.

|Метод|Описание|
|------------|-----------------|
|[Attach](../../../extensibility/debugger/reference/idebugprocessex2-attach.md)|Информирует процесс о том, что сеанс теперь отлажет процесс.|
|[Detach](../../../extensibility/debugger/reference/idebugprocessex2-detach.md)|Информирует процесс о том, что сеанс больше не отлаживает процесс.|
|[AddImplicitProgramNodes](../../../extensibility/debugger/reference/idebugprocessex2-addimplicitprogramnodes.md)|Добавляет узлы программы для списка отладоть двигатели.|

## <a name="remarks"></a>Примечания
 Этот интерфейс является закрытым между SDM и процессом.

## <a name="requirements"></a>Требования
 Заголовок: Portpriv.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
