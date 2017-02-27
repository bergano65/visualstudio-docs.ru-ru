---
title: "Метод GetScheduledTasksForDebugger | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Метод GetScheduledTasksForDebugger, класс TaskScheduler [обработчиков отладки платформы .NET Framework]"
ms.assetid: 7c9b4cde-6e4a-4cef-929f-7d02b1da5762
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Метод GetScheduledTasksForDebugger
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Возвращает массив всех запланированных заданий.  
  
 **Пространство имен:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Сборки:** mscorlib \(в библиотеке mscorlib.dll\)  
  
 Так как не удается получить доступ к внутреннему элементу из платформы .NET Framework, следующий синтаксис предоставляется общего промежуточного языка \(CIL\).  
  
## Синтаксис  
  
```  
.method assembly hidebysig instance class System.Threading.Tasks.Task[] GetScheduledTasksForDebugger() cil managed  
```  
  
## Возвращаемое значение  
 Массив всех запланированных задач. Каждая задача выполняется или завершена.  
  
## Заметки  
 Этот метод не является потокобезопасным и не должны использоваться параллельно с других экземпляров <xref:System.Threading.Tasks.TaskScheduler> она должна вызываться из отладчика только в том случае, если отладчик приостановил других потоков.  
  
## См. также  
 [Класс TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)