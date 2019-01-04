---
title: Модель для пакетов управления исходным кодом | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], model
ms.assetid: 6164b2d3-a622-4de8-bef3-a6de985e9ebd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 992fd9a6f45d607538f1091eb7a652984595cc34
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53954504"
---
# <a name="model-for-source-control-packages"></a>Модель для пакетов системы управления версиями
Следующая модель представляет пример реализации элемента управления источника. В модели вы увидите, интерфейсы, которые необходимо реализовать и службам среды выполнения, которые необходимо вызвать. Как и все службы фактически вызывать методы класса определенного интерфейса, полученный посредством службы. Имена классов определяются для упрощения см. в разделе способ выполнения системы управления версиями.  
  
 ![SCC&#95;примеры ТРОЙКИ](../../extensibility/internals/media/scc_tup.gif "SCC_TUP")  
Проекта системы управления версиями пример  
  
## <a name="interfaces"></a>интерфейсов,  
 Вы можете реализовать систему управления версиями для новых типов проекта в Visual Studio, используя список интерфейсов, показано в следующей таблице.  
  
|Интерфейс|Использовать|  
|---------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|Вызывается средой проектов и редакторов до их сохранения или файлы изменений ("грязный"). Этот интерфейс осуществляется с помощью <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> службы.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Вызывается проектами, чтобы запросить разрешение на добавление, удаление или переименование файла или каталога. Этот интерфейс также вызывается проектами, чтобы сообщить о том, что среде при утвержденных add, удалить или переименовать действие завершено. Осуществляется с помощью <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> службы.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|Реализуется Любая сущность, которая регистрирует получать уведомления при проектов добавить, переименовать или удалить файл или каталог. Чтобы зарегистрироваться для уведомления о событии, вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Вызывается проектами для регистрации пакета системы управления версиями и получить сведения о состояния системы управления версиями. Этот интерфейс осуществляется с помощью <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> службы.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Реализуется проектом, реагировать на запросы системы управления версиями сведения о файлах и получить источник параметров управления, необходимых для файла проекта.|  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 [Поддержка системы управления версиями](../../extensibility/internals/supporting-source-control.md)