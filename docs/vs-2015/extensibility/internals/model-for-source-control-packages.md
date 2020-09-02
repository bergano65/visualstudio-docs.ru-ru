---
title: Модель для пакетов управления версиями | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], model
ms.assetid: 6164b2d3-a622-4de8-bef3-a6de985e9ebd
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 811cdfa2cbae85d6509e7cd883c5675b81639fa0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198434"
---
# <a name="model-for-source-control-packages"></a>Модель для пакетов системы управления версиями
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

В следующей модели представлен пример реализации системы управления версиями. В модели отображаются интерфейсы, которые необходимо реализовать, и службы среды, которые необходимо вызвать. Как и все службы, в действительности вызываются методы определенного интерфейса, получаемые посредством службы. Имена классов идентифицируются, чтобы упростить просмотр управления исходным кодом.  
  
 ![Примеры SCC&#95;ТРОЙКИ](../../extensibility/internals/media/scc-tup.gif "SCC_TUP")  
Пример проекта системы управления версиями  
  
## <a name="interfaces"></a>Интерфейсы  
 Вы можете реализовать систему управления версиями для новых типов проектов в Visual Studio, используя список интерфейсов, приведенных в следующей таблице.  
  
|Интерфейс|Использовать|  
|---------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|Вызывается проектами и редакторами перед сохранением или изменением (грязных) файлов. Доступ к этому интерфейсу осуществляется с помощью <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> службы.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Вызывается проектами для запроса разрешения на добавление, удаление или переименование файла или каталога. Этот интерфейс также вызывается проектами для информирования среды о завершении утвержденного действия Add, Remove или Rename. Доступ к нему осуществляется с помощью <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> службы.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|Реализуется любой сущностью, которая регистрируется для получения уведомления о добавлении, переименовании или удалении файла или каталога в проектах. Чтобы зарегистрироваться для получения уведомления о событии, вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A> .|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Вызывается проектами для регистрации в пакете системы управления версиями и получения сведений о состоянии системы управления версиями. Доступ к этому интерфейсу осуществляется с помощью <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> службы.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Реализуется проектом для реагирования на запросы системы управления версиями на получение сведений о файлах и получения параметров системы управления версиями, необходимых для файла проекта.|  
  
## <a name="see-also"></a>См. также:  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 [Поддержка системы управления версиями](../../extensibility/internals/supporting-source-control.md)
