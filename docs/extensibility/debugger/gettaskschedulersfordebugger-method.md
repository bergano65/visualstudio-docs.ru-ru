---
title: "Метод GetTaskSchedulersForDebugger | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Метод GetTaskSchedulersForDebugger, класс TaskScheduler [обработчиков отладки платформы .NET Framework]"
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Метод GetTaskSchedulersForDebugger
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Получает массив всех <xref:System.Threading.Tasks.TaskScheduler> объектов, которые активны в данный момент.  
  
 **Пространство имен:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Сборки:** mscorlib \(в библиотеке mscorlib.dll\)  
  
 Так как не удается получить доступ к внутреннему элементу из платформы .NET Framework, следующий синтаксис предоставляется общего промежуточного языка \(CIL\).  
  
## Синтаксис  
  
```  
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed  
```  
  
## Возвращаемое значение  
 Массив всех <xref:System.Threading.Tasks.TaskScheduler> объектов, которые активны в данный момент в этом <xref:System.AppDomain>.  
  
## Заметки  
 Этот метод не является потокобезопасным и не должны использоваться параллельно с других экземпляров <xref:System.Threading.Tasks.TaskScheduler>. Его следует вызывать из отладчика, только в том случае, если отладчик приостановил других потоков.  
  
## См. также  
 [Класс TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)