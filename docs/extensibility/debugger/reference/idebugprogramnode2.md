---
title: IDebugProgramNode2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2
helpviewer_keywords:
- IDebugProgramNode2 interface
ms.assetid: 80e511d8-9b40-4a85-aa5d-952fa5ee6ae7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2e6eac7c97b9d375f32e36a372d6f31175c79098
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721913"
---
# <a name="idebugprogramnode2"></a>IDebugProgramNode2
Этот интерфейс представляет собой программу, которую можно отладить.

## <a name="syntax"></a>Синтаксис

```
IDebugProgramNode2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Отладка двигателя (DE) или пользовательский поставщик порта реализует этот интерфейс для представления программы, которая может быть отлажена. Этот интерфейс обычно реализуется на том же объекте, который реализует интерфейс [IDebugProgram2.](../../../extensibility/debugger/reference/idebugprogram2.md) Этот интерфейс зарегистрирован [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] по телефону [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md).

## <a name="notes-for-callers"></a>Заметки для абонентов
 Позвоните [GetProviderProgramNode,](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) чтобы вернуть этот интерфейс. Поставщик пользовательских портов получает этот интерфейс через звонок [в AddProgramNode.](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) DE получает этот интерфейс через вызов [для присоединения.](../../../extensibility/debugger/reference/idebugengine2-attach.md)

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugProgramNode2`.

|Метод|Описание|
|------------|-----------------|
|[GetProgramName](../../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)|Получает название программы.|
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)|Получает название процесса размещения программы.|
|[GetHostPid](../../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)|Получает идентификатор системного процесса для процесса размещения программы.|
|[GetHostMachineName_V7](../../../extensibility/debugger/reference/idebugprogramnode2-gethostmachinename-v7.md)|Устаревшие. НЕ ИСПОЛЬЗУЙТЕ.|
|[Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)|Устаревшие. НЕ ИСПОЛЬЗУЙТЕ. Ознакомиться с интерфейсом [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) можно поальтернативным.|
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)|Получает имя и идентификатор DE, запуская эту программу.|
|[DetachDebugger_V7](../../../extensibility/debugger/reference/idebugprogramnode2-detachdebugger-v7.md)|Устаревшие. НЕ ИСПОЛЬЗУЙТЕ.|

## <a name="remarks"></a>Примечания
 Менеджер отладки сеанса (SDM) обычно вызывает [GetProviderProgramNode,](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) чтобы получить этот интерфейс.

## <a name="requirements"></a>Требования
 Заголовок: Msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
- [RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)
- [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)
