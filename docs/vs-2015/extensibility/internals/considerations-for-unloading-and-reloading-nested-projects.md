---
title: Рекомендации по выгрузке и перезагрузке вложенных проектов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 65145530c8cd6b68b82391a09b395bb8c9a61117
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197004"
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>Рекомендации по выгрузке и перезагрузке вложенных проектов
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

При реализации вложенных типов проектов необходимо выполнить дополнительные действия при выгрузке и перезагрузке проектов. Чтобы правильно уведомить прослушиватели о событиях решения, необходимо правильно вызвать `OnBeforeUnloadProject` `OnAfterLoadProject` события и.  
  
 Одна из причин, по которой необходимо создать эти события, заключается в том, что не нужно, чтобы средство управления исходным кодом удалило элементы с сервера, а затем снова добавили их, если в SCC имеется `Get` операция. В этом случае новый файл будет загружен из SCC и необходимо будет выгружать и перезагружать все файлы на случай, если они отличаются. Вызовы SCC `ReloadItem` . Реализация этого вызова заключается в удалении проекта и повторном его создании путем реализации `IVsFireSolutionEvents` для вызова `OnBeforeUnloadProject` и `OnAfterLoadProject` . При выполнении этой реализации средство SCC сообщает о том, что проект был временно удален и добавлен снова. Таким образом, SCC не работает с проектом так, как если бы проект был фактически удален с сервера, а затем добавлен снова.  
  
## <a name="reloading-projects"></a>Перезагрузка проектов  
 Для поддержки перезагрузки вложенных проектов необходимо реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> метод. В реализации `ReloadItem` вы закрываете вложенные проекты, а затем создаете их повторно.  
  
 Как правило, при повторной загрузке проекта интегрированная среда разработки создает <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> события и `M:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject(Microsoft.VisualStudio.Shell.Interop.IVsHierarchy,Microsoft.VisualStudio.Shell.Interop.IVsHierarchy)` . Однако для вложенных проектов, которые будут удалены и перезагружены, родительский проект запускает процесс, а не интегрированную среду разработки. Так как родительский проект не вызывает события решения, а в интегрированной среде разработки нет сведений об инициализации процесса, события не вызываются.  
  
 Для обработки этого процесса родительский проект вызывает `QueryInterface` <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> интерфейс из интерфейса <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> . `IVsFireSolutionEvents` содержит функции, которые сообщают интегрированной среде разработки о необходимости вызова `OnBeforeUnloadProject` события для выгрузки вложенного проекта, а затем вызывают `OnAfterLoadProject` событие для повторной загрузки того же проекта.  
  
## <a name="see-also"></a>См. также:  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 [Проекты вложения](../../extensibility/internals/nesting-projects.md)
