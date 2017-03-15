---
title: "Рекомендации по выгрузка и перезагрузка вложенных проектов | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "вложенные проекты, выгрузки и загрузки"
  - "проекты [Visual Studio SDK] выгрузки и загрузки вложенные"
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Рекомендации по выгрузка и перезагрузка вложенных проектов
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

При реализации вложенные типы проектов, следует выполнить дополнительные шаги при разгржаете и перезагрузите проекты.  Верно для уведомления прослушивателей на события решения, необходимо правильно вызвать `OnBeforeUnloadProject` и  `OnAfterLoadProject` события.  
  
 Одной из причин необходимо вызвать эти события таким образом, что не требуется, чтобы элемент управления исходным кодом \(SCC\) удаление элементов с сервера, а затем добавлять их в виде если что\-то новое a `Get` операция от SCC.  В этом случае новый файл будет загружен из SCC и необходимо выгрузить и перезапустить все файлы в случае, если они различаются.  Вызовы SCC `ReloadItem`.  Реализация этого вызова удалить проект и затем повторно создать его повторно путем реализации `IVsFireSolutionEvents` вызов  `OnBeforeUnloadProject` и  `OnAfterLoadProject`.  При выполнении этой реализации, SCC информирован, что проект был временно удаляется, и был добавлен.  Поэтому SCC не обрабатывает проект, если проект был фактически удален с сервера, а затем добавляется еще раз.  
  
## Перезагрузить проекты  
 Для поддержки перезапустить вложенных проектов необходимо реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> метод.  В реализации `ReloadItem`нажмите закрыть вложенных проектов и затем повторно создать их.  
  
 Обычно при перезапуске проекта интегрированная среда разработки вызывает `M:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject(Microsoft.VisualStudio.Shell.Interop.IVsHierarchy,Microsoft.VisualStudio.Shell.Interop.IVsHierarchy)` и  <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> события.  Однако для вложенных проектов, которые будут удалены и перезапускаются, родительский проект инициирует процесс, не интегрированной среды разработки.  Поскольку родительский проект не вызывает события решения и интегрированная среда разработки не имеет сведений об инициализации процесса, события не вызываются.  
  
 Настроить этот процесс обращения родительского проекта `QueryInterface` на  <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> интерфейс с  <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> интерфейс.  `IVsFireSolutionEvents` содержит функции, которые настраивают интегрированная среда разработки вызывает  `OnBeforeUnloadProject` событие для выгрузки вложенный проект, а затем вызвать  `OnAfterLoadProject` событие, для которого необходимо перезапустить один и тот же проект.  
  
## См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 [Вложенность проектов](../../extensibility/internals/nesting-projects.md)