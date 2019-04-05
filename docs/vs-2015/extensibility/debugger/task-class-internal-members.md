---
title: 'Внутренние элементы: класс Task | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, Task class [.NET Framework]
- Task class [.NET Framework debug engines]
ms.assetid: 28e47c3b-9323-424a-80ac-6cc3bf19e09b
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 200b35e60d3d468a934565959629298e6c6f04bf
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58994516"
---
# <a name="task-class---internal-members"></a>Внутренние элементы: класс Task
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

В этом разделе описывается внутренним членам объектов <xref:System.Threading.Tasks.Task?displayProperty=fullName> класс, который помогут вам реализовать пользовательского отладчика. Общие сведения об этом классе см. в разделе <xref:System.Threading.Tasks.Task> справочника.  
  
 **Пространство имен:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Сборка:** mscorlib (в mscorlib.dll)  
  
 Так как при отсутствии доступа к этим внутренним членам платформы .NET Framework, следующий синтаксис предоставляется общего промежуточного языка (CIL).  
  
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
  
|name|Описание|  
|----------|-----------------|  
|[Метод SetNotificationForWaitCompletion](../../extensibility/debugger/setnotificationforwaitcompletion-method.md)|Задает или сбрасывает бит TASK_STATE_WAIT_COMPLETION_NOTIFICATION состояния.|  
|[Метод NotifyDebuggerOfWaitCompletion](../../extensibility/debugger/notifydebuggerofwaitcompletion-method.md)|Метод заполнитель, используемый как целевой объект точки останова в отладчике.|  
  
### <a name="fields"></a>Поля  
  
|name|Описание|  
|----------|-----------------|  
|[m_action](../../extensibility/debugger/m-action-field.md)|Делегат, который представляет код, выполняемый в <xref:System.Threading.Tasks.Task> объекта.|  
|[m_contingentProperties](../../extensibility/debugger/m-contingentproperties-field.md)|Хранит дополнительные свойства <xref:System.Threading.Tasks.Task> объекта.|  
|[m_parent](../../extensibility/debugger/m-parent-field.md)|Резервное поле для <xref:System.Threading.Tasks.Task?displayProperty=fullName> родительского свойства.|  
|[m_stateFlags](../../extensibility/debugger/m-stateflags-field.md)|Хранит сведения о текущем состоянии <xref:System.Threading.Tasks.Task> объекта.|  
|[m_stateObject](../../extensibility/debugger/m-stateobject-field.md)|Объект, представляющий данные, которые будут использоваться для действия.|  
|[m_taskId](../../extensibility/debugger/m-taskid-field.md)|Резервное поле для <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=fullName> свойство.|  
|[s_taskIdCounter](../../extensibility/debugger/s-taskidcounter-field.md)|Следующий доступный идентификатор для <xref:System.Threading.Tasks.Task> объекта.|  
|[TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)|Указывает, что задача была отменена, прежде чем он достигнет запущена или что задача приняла отмену его и без исключений.|  
|[TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)|Указывает, что задача выполняется.|  
|[TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)|Указывает, что задача завершена из-за необработанного исключения.|  
|[TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)|Указывает, что задача успешно завершена.|  
|[TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)|Указывает, что задача закончила выполнение его делегат и неявно ожидает завершения присоединенных дочерних задач.|  
  
## <a name="remarks"></a>Примечания  
 Следующие внутренние методы полезны для обработчика отладки, поскольку эти файлы обозначают входом <xref:System.Threading.Tasks.Task> выполнение кода:  
  
-   `Execute`  
  
-   `ExecuteEntry`  
  
-   `ExecuteWithThreadLocal`  
  
-   `Finish`  
  
-   `InnerInvoke`  
  
-   `InternalWait`  
  
## <a name="see-also"></a>См. также  
 <xref:System.Threading.Tasks.Task?displayProperty=fullName>   
 [Внутренние компоненты параллельных расширений для .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
