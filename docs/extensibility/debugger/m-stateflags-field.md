---
title: "m_stateFlags поля | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "поле m_stateFlags, класс задачи [обработчиков отладки платформы .NET Framework]"
ms.assetid: 82b20efc-08f2-4cd2-91f6-4e01e3da906b
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# m_stateFlags поля
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Хранит сведения о текущем состоянии <xref:System.Threading.Tasks.Task> объекта.  
  
 **Пространство имен:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Сборки:** mscorlib \(в библиотеке mscorlib.dll\)  
  
 Так как не удается получить доступ к внутреннему элементу из платформы .NET Framework, следующий синтаксис предоставляется общего промежуточного языка \(CIL\).  
  
## Синтаксис  
  
```  
.field assembly int32 modreq(System.Runtime.CompilerServices.IsVolatile) m_stateFlags  
```  
  
## Заметки  
 Как правило, используется <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=fullName> свойство для доступа к этому значению.  
  
 Этот член может быть сочетанием следующих значений:  
  
-   [TASK\_STATE\_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)  
  
-   [TASK\_STATE\_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)  
  
-   [TASK\_STATE\_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)  
  
-   [TASK\_STATE\_WAITING\_ON\_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)  
  
-   [TASK\_STATE\_RAN\_TO\_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)  
  
## См. также  
 [Класс Task](../../extensibility/debugger/task-class-internal-members.md)