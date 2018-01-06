---
title: "Рекомендации для выгрузки и загрузки вложенные проекты | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fd45ebf8be2732cded5c84f18338f104b76840cf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>Рекомендации по выгрузка и перезагрузка проектов вложенные
При реализации проекта вложенные типы должны выполнения дополнительных действий при выгрузить и перезагрузить проекты. Правильно уведомляла прослушивателями событий решения, необходимо правильно повысить `OnBeforeUnloadProject` и `OnAfterLoadProject` события.  
  
 Один этих событий, таким образом, необходимо изменить обусловлено тем, что вы не хотите, управления исходным кодом (SCC), чтобы удалить элементы с сервера, а затем добавьте их обратно в качестве нововведения при наличии `Get` операции SCC. В этом случае новый файл загружается из SCC и необходимо выгрузить и снова загрузить файлы, если они отличаются. Вызовы SCC `ReloadItem`. Реализации этого вызова является удаление проекта и повторно создать его путем реализации `IVsFireSolutionEvents` для вызова `OnBeforeUnloadProject` и `OnAfterLoadProject`. При выполнении этой реализации, SCC получает сведения, что проект был временно удалить и снова добавить. Таким образом SCC не работает в проекте как в том случае, если проект был фактически удален с сервера, а затем добавить его.  
  
## <a name="reloading-projects"></a>Перезагрузка проектов  
 Для поддержки перезагрузке вложенных проектов, необходимо реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> метод. В реализации `ReloadItem`, закройте вложенных проектов и создайте их заново.  
  
 Обычно при перезагрузке проекта IDE вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> и `M:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject(Microsoft.VisualStudio.Shell.Interop.IVsHierarchy,Microsoft.VisualStudio.Shell.Interop.IVsHierarchy)` события. Однако для вложенных проектов, которые будут удалены и повторно загрузить, родительского проекта инициирует процесс, не интегрированной среды разработки. Так как родительский проект, не порождает событий решения и интегрированной среды разработки не содержит сведений об инициализации процесса, события не вызываются.  
  
 Для обработки этого процесса вызовы родительский проект `QueryInterface` на <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> интерфейса. `IVsFireSolutionEvents`содержит функции, сообщающие интегрированной среды разработки для вызова `OnBeforeUnloadProject` событий для выгрузки вложенный проект и затем вызвать `OnAfterLoadProject` событий перезагрузить одного проекта.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 [Проекты вложения](../../extensibility/internals/nesting-projects.md)