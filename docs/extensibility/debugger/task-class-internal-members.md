---
title: "Класс - внутренним членам Task | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, Task class [.NET Framework]
- Task class [.NET Framework debug engines]
ms.assetid: 28e47c3b-9323-424a-80ac-6cc3bf19e09b
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 21acb0a52dfde7ad565e9764e2a333a9925a2171
ms.lasthandoff: 02/22/2017

---
# <a name="task-class---internal-members"></a>Класс Task - внутренние члены
В этом разделе описываются внутренним элементам <xref:System.Threading.Tasks.Task?displayProperty=fullName>классов, которые помогают реализовать пользовательские отладчика.</xref:System.Threading.Tasks.Task?displayProperty=fullName> Общие сведения об этом классе см. в разделе <xref:System.Threading.Tasks.Task>раздел справки.</xref:System.Threading.Tasks.Task>  
  
 **Пространство имен:**<xref:System.Threading.Tasks?displayProperty=fullName></xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Сборка:** mscorlib (в библиотеке mscorlib.dll)  
  
 Поскольку невозможно получить эти внутренние члены из платформы .NET Framework, следующий синтаксис предоставляется общего промежуточного языка (CIL).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
.class public auto ansi System.Threading.Tasks.Task  
       extends System.Object  
       implements System.Threading.IThreadPoolWorkItem,  
                  System.IAsyncResult,  
                  System.IDisposable,  
                  System.Threading.ICancelableOperation  
```  
  
## <a name="members"></a>Члены  
  
### <a name="methods"></a>Методы  
  
|Имя|Описание|  
|----------|-----------------|  
|[Метод SetNotificationForWaitCompletion](../../extensibility/debugger/setnotificationforwaitcompletion-method.md)|Устанавливает или снимает бит TASK_STATE_WAIT_COMPLETION_NOTIFICATION состояния.|  
|[Метод NotifyDebuggerOfWaitCompletion](../../extensibility/debugger/notifydebuggerofwaitcompletion-method.md)|Заполнитель метод используется в качестве цели точки останова в отладчике.|  
  
### <a name="fields"></a>Поля  
  
|Имя|Описание|  
|----------|-----------------|  
|[обращение](../../extensibility/debugger/m-action-field.md)|Делегат, который представляет код, выполняемый в <xref:System.Threading.Tasks.Task>объекта.</xref:System.Threading.Tasks.Task>|  
|[m_contingentProperties](../../extensibility/debugger/m-contingentproperties-field.md)|Хранит дополнительные свойства <xref:System.Threading.Tasks.Task>объекта.</xref:System.Threading.Tasks.Task>|  
|[m_parent](../../extensibility/debugger/m-parent-field.md)|Резервное поле для <xref:System.Threading.Tasks.Task?displayProperty=fullName>свойство parent.</xref:System.Threading.Tasks.Task?displayProperty=fullName>|  
|[m_stateFlags](../../extensibility/debugger/m-stateflags-field.md)|Хранит сведения о текущем состоянии <xref:System.Threading.Tasks.Task>объекта.</xref:System.Threading.Tasks.Task>|  
|[m_stateObject](../../extensibility/debugger/m-stateobject-field.md)|Объект, представляющий данные, которые будут использоваться действие.|  
|[m_taskId типа](../../extensibility/debugger/m-taskid-field.md)|Резервное поле для <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=fullName>свойство.</xref:System.Threading.Tasks.Task.Id%2A?displayProperty=fullName>|  
|[s_taskIdCounter типа](../../extensibility/debugger/s-taskidcounter-field.md)|Следующий доступный идентификатор для <xref:System.Threading.Tasks.Task>объекта.</xref:System.Threading.Tasks.Task>|  
|[TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)|Указывает, что выполнение задачи было отменено до его достижения запущена или что задача приняла его отмену и завершена без исключения.|  
|[TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)|Указывает, что задача выполняется.|  
|[TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)|Указывает, что задача была завершена из-за необработанного исключения.|  
|[TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)|Указывает, что задача завершена успешно.|  
|[TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)|Указывает, что задача закончила выполнение своего делегата и неявно ожидает завершения присоединенных дочерних задач.|  
  
## <a name="remarks"></a>Примечания  
 Следующие внутренние методы полезны для ядра отладчика, поскольку они указывают входом <xref:System.Threading.Tasks.Task>выполнение кода:</xref:System.Threading.Tasks.Task>  
  
-   `Execute`  
  
-   `ExecuteEntry`  
  
-   `ExecuteWithThreadLocal`  
  
-   `Finish`  
  
-   `InnerInvoke`  
  
-   `InternalWait`  
  
## <a name="see-also"></a>См. также  
 <xref:System.Threading.Tasks.Task?displayProperty=fullName></xref:System.Threading.Tasks.Task?displayProperty=fullName>   
 [Внутренние компоненты параллельных расширений для .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
