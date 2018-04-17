---
title: Класс - внутренние члены Task | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, Task class [.NET Framework]
- Task class [.NET Framework debug engines]
ms.assetid: 28e47c3b-9323-424a-80ac-6cc3bf19e09b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 161572ece44f3a9f07c9eb40638ca98170e3a86c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="task-class---internal-members"></a>Класс задачи - внутренние элементы
В этом разделе описывает внутренние элементы <xref:System.Threading.Tasks.Task?displayProperty=fullName> класса, которые помогут реализовать пользовательского отладчика. Общие сведения об этом классе см. в разделе <xref:System.Threading.Tasks.Task> справочном разделе.  
  
 **Пространство имен:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Сборка:** mscorlib (в библиотеке mscorlib.dll)  
  
 Так как не удается получить доступ к эти внутренние члены из платформы .NET Framework, синтаксиса предоставляется общего промежуточного языка (CIL).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
.class public auto ansi System.Threading.Tasks.Task  
       extends System.Object  
       implements System.Threading.IThreadPoolWorkItem,  
                  System.IAsyncResult,  
                  System.IDisposable,  
                  System.Threading.ICancelableOperation  
```  
  
## <a name="members"></a>Участники  
  
### <a name="methods"></a>Методы  
  
|Имя|Описание|  
|----------|-----------------|  
|[Метод SetNotificationForWaitCompletion](../../extensibility/debugger/setnotificationforwaitcompletion-method.md)|Устанавливает или снимает бит TASK_STATE_WAIT_COMPLETION_NOTIFICATION состояния.|  
|[Метод NotifyDebuggerOfWaitCompletion](../../extensibility/debugger/notifydebuggerofwaitcompletion-method.md)|Метод заполнителя, используется как целевой объект точки останова в отладчике.|  
  
### <a name="fields"></a>Поля  
  
|name|Описание|  
|----------|-----------------|  
|[обращение](../../extensibility/debugger/m-action-field.md)|Делегат, который представляет код, выполняемый в <xref:System.Threading.Tasks.Task> объекта.|  
|[m_contingentProperties](../../extensibility/debugger/m-contingentproperties-field.md)|Хранит дополнительные свойства <xref:System.Threading.Tasks.Task> объекта.|  
|[m_parent](../../extensibility/debugger/m-parent-field.md)|Резервное поле для <xref:System.Threading.Tasks.Task?displayProperty=fullName> родительского свойства.|  
|[m_stateFlags](../../extensibility/debugger/m-stateflags-field.md)|Хранит сведения о текущем состоянии <xref:System.Threading.Tasks.Task> объекта.|  
|[m_stateObject](../../extensibility/debugger/m-stateobject-field.md)|Объект, представляющий данные, которые будут использоваться для действия.|  
|[m_taskId типа](../../extensibility/debugger/m-taskid-field.md)|Резервное поле для <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=fullName> свойства.|  
|[s_taskIdCounter типа](../../extensibility/debugger/s-taskidcounter-field.md)|Следующий доступный идентификатор для <xref:System.Threading.Tasks.Task> объекта.|  
|[TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)|Указывает, что задача была отменена до его достижения запущена или, что задача приняла отмену его и завершена без исключения.|  
|[TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)|Указывает, что задача выполняется.|  
|[TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)|Указывает, что задача была завершена из-за необработанного исключения.|  
|[TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)|Указывает, что задача завершена успешно.|  
|[TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)|Указывает, что задача закончила выполнение своего делегата и неявно ожидает завершения присоединенных дочерних задач.|  
  
## <a name="remarks"></a>Примечания  
 Следующие внутренние методы полезны для обработчика отладки, так как они указывают входом <xref:System.Threading.Tasks.Task> выполнение кода:  
  
-   `Execute`  
  
-   `ExecuteEntry`  
  
-   `ExecuteWithThreadLocal`  
  
-   `Finish`  
  
-   `InnerInvoke`  
  
-   `InternalWait`  
  
## <a name="see-also"></a>См. также  
 <xref:System.Threading.Tasks.Task?displayProperty=fullName>   
 [Внутренние компоненты параллельных расширений для .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)