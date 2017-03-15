---
title: "Модель для пакетов управления версиями | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "модель управления версиями файлов [Visual Studio SDK]"
ms.assetid: 6164b2d3-a622-4de8-bef3-a6de985e9ebd
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Модель для пакетов управления версиями
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Следующая модель представляет пример реализации системы управления версиями.  В модели отображаются интерфейсы, которые необходимо реализовать и службы среды, необходимо вызвать.  Как и все службы, фактически вызовите методы указанного интерфейса, полученные через службы.  Имена классов, определенных для упрощения увидеть, как система управления версиями унесена.  
  
 ![SCC&#95;TUP примеры](../../extensibility/internals/media/scc_tup.png "SCC\_TUP")  
Проект из системы управления версиями примера  
  
## Интерфейсы  
 Можно реализовать систему управления версиями для новых типов проектов в Visual Studio, используя список интерфейсов, приведенных в следующей таблице.  
  
|Интерфейс|Применение|  
|---------------|----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|Вызывается проектами и редакторами перед их сохранение изменений \(\) или измененные файлы.  Этот интерфейс, доступ к которому можно получить с помощью <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> служба.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Вызывается проектами запросить разрешение на добавление, удаление или переименуйте файл или каталог.  Этот интерфейс также вызывается проектами среде, когда ок добавить, удаляет или переименовывает действие завершено.  Он получить доступ с помощью <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> служба.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|Реализуется любой сущностью, которая регистрирует быть получать извещения об изменениях проектов добавляют, переименовать или удалить файл или каталог.  Для регистрации для уведомления о событии, вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Вызывается проектами зарегистрировать с пакетом системы управления версиями и получения сведений о состоянии системы управления версиями.  Этот интерфейс, доступ к которому можно получить с помощью <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> служба.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Реализуется проектом отвечать на запросы системы управления версиями дополнительные сведения о файлах и получить параметры системы управления версиями, необходимые для файла проекта.|  
  
## См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 [Поддержка системы управления версиями](../../extensibility/internals/supporting-source-control.md)