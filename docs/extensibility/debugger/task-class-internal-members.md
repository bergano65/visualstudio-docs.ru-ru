---
title: Класс задач - Внутренние члены Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, Task class [.NET Framework]
- Task class [.NET Framework debug engines]
ms.assetid: 28e47c3b-9323-424a-80ac-6cc3bf19e09b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dcf278c0248b344cea4be7cf161ecc91581f5f2e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712738"
---
# <a name="task-class---internal-members"></a>Класс задач - внутренние члены
В этой статье описаны <xref:System.Threading.Tasks.Task?displayProperty=fullName> внутренние члены класса, которые помогают реализовать пользовательский отладчик. Для получения общей информации <xref:System.Threading.Tasks.Task> об этом классе см.

 **Пространство имен:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Сборка:** mscorlib (в *mscorlib.dll*)

 Поскольку вы не можете получить доступ к этим внутренним членам из рамочного соглашения .NET, следующий синтаксис предоставляется на общем промежуточном языке (CIL).

## <a name="syntax"></a>Синтаксис

```csharp
.class public auto ansi System.Threading.Tasks.Task
       extends System.Object
       implements System.Threading.IThreadPoolWorkItem,
                  System.IAsyncResult,
                  System.IDisposable,
                  System.Threading.ICancelableOperation
```

## <a name="members"></a>Участники

### <a name="methods"></a>Методы

|name|Описание|
|----------|-----------------|
|[Метод SetNotificationForWaitCompletion](../../extensibility/debugger/setnotificationforwaitcompletion-method.md)|Устанавливает или очищает TASK_STATE_WAIT_COMPLETION_NOTIFICATION бит состояния.|
|[Метод NotifyDebuggerOfWaitCompletion](../../extensibility/debugger/notifydebuggerofwaitcompletion-method.md)|Метод заплатиса, используемый в качестве цели точки разрыва отладчиком.|

### <a name="fields"></a>Поля

|name|Описание|
|----------|-----------------|
|[m_action](../../extensibility/debugger/m-action-field.md)|Делегат, представляющий код для <xref:System.Threading.Tasks.Task> выполнения в объекте.|
|[m_contingentProperties](../../extensibility/debugger/m-contingentproperties-field.md)|Хранит дополнительные <xref:System.Threading.Tasks.Task> свойства объекта.|
|[m_parent](../../extensibility/debugger/m-parent-field.md)|Резервное поле <xref:System.Threading.Tasks.Task?displayProperty=fullName> для родительского свойства.|
|[m_stateFlags](../../extensibility/debugger/m-stateflags-field.md)|Хранит информацию о текущем <xref:System.Threading.Tasks.Task> состоянии объекта.|
|[m_stateObject](../../extensibility/debugger/m-stateobject-field.md)|Объект, представляющий данные, которые будут использоваться действием.|
|[m_taskId](../../extensibility/debugger/m-taskid-field.md)|Резервное <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=fullName> поле для свойства.|
|[s_taskIdCounter](../../extensibility/debugger/s-taskidcounter-field.md)|Следующий доступный <xref:System.Threading.Tasks.Task> идентификатор для объекта.|
|[TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)|Указывается, что задача отменена до достижения запущенного состояния или что задача подтвердила ее отмену и завершилась без исключения.|
|[TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)|Означает, что задача запущена.|
|[TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)|Указано, что задача выполнена из-за необработанного исключения.|
|[TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)|Означает, что задача успешно выполнена.|
|[TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)|Означает, что задача завершила выполнение своего делегата и неявно ждет завершения прилагаемых детских задач.|

## <a name="remarks"></a>Примечания
 Следующие внутренние методы полезны для двигателя отладчика, поскольку они обозначают вход в <xref:System.Threading.Tasks.Task> выполнение кода:

- `Execute`

- `ExecuteEntry`

- `ExecuteWithThreadLocal`

- `Finish`

- `InnerInvoke`

- `InternalWait`

## <a name="see-also"></a>См. также
- <xref:System.Threading.Tasks.Task?displayProperty=fullName>
- [Параллельные внутренние расширения для рамочной программы .NET](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
