---
title: "Для пакетов управления версиями | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control [Visual Studio SDK], model
ms.assetid: 6164b2d3-a622-4de8-bef3-a6de985e9ebd
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1960b5fe7b7c507b5b3275315ea6ae1715c27f76
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="model-for-source-control-packages"></a>Модель для пакетов управления версиями
Следующая модель представляет пример реализации элемента управления источника. В модели можно увидеть, интерфейсы, которые должны быть реализованы и среды служб, которые необходимо вызвать. Как и все службы фактически вызова методов определенный интерфейс, который можно получить посредством службы. Имена классов определяются для упрощения разделе способ выполнения системы управления версиями.  
  
 ![SCC &#95; Примеры TUP](../../extensibility/internals/media/scc_tup.gif "SCC_TUP")  
Пример проекта системы управления версиями  
  
## <a name="interfaces"></a>интерфейсов,  
 Система управления версиями можно реализовать для вашего новых типов проектов в Visual Studio, используя список интерфейсов, показанные в следующей таблице.  
  
|Интерфейс|Использовать|  
|---------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|Вызывается по проектам и редакторы перед их сохранения или файлы изменение («грязные»). Этот интерфейс осуществляется с помощью <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> службы.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Вызывается проектами, чтобы запросить разрешение на добавление, удаление или переименование файла или каталога. Этот интерфейс также вызывается проекты, чтобы сообщить среде при утвержденных сложения, удаление или переименование действия выполнена. Осуществляется с помощью <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> службы.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|Реализован Любая сущность, которая регистрируется для уведомления о проектах добавить, переименовать или удалить файл или каталог. Чтобы зарегистрироваться для уведомления о событии, вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Вызывается проектами для регистрации с помощью пакета управления версиями и получить сведения о состоянии элемента управления источника. Этот интерфейс осуществляется с помощью <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> службы.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Реализован проекта отвечает на запросы системы управления версиями для получения сведений о файлах и получить источник параметров управления, необходимых для файла проекта.|  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 [Поддержка системы управления версиями](../../extensibility/internals/supporting-source-control.md)