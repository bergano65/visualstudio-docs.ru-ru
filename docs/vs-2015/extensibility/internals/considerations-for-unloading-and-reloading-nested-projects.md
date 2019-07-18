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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68197004"
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>Рекомендации по выгрузке и перезагрузке вложенных проектов
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

При реализации типов вложенных проектов, необходимо выполнить дополнительные действия, когда Вы выгрузите, а затем перезагрузить проекты. Чтобы правильно уведомлять прослушивателей событий решения, нужно правильно повысить `OnBeforeUnloadProject` и `OnAfterLoadProject` события.  
  
 Одна из причин, необходимо изменить эти события таким образом, что делает не системы управления исходным кодом (SCC), чтобы удалить элементы с сервера, а затем добавьте на их обратно как что-то новое, если имеется `Get` операции SCC. В этом случае загружается новый файл из SCC, и вам придется выгружать и загружать файлы, если они отличаются. Вызовы SCC `ReloadItem`. Реализации этого вызова является удаление проекта и повторно создайте его заново, реализовав `IVsFireSolutionEvents` для вызова `OnBeforeUnloadProject` и `OnAfterLoadProject`. При выполнении этой реализации, SCC получает сведения проекта была временно удалена и снова добавить. Таким образом SCC не работают с проекта, как в том случае, если проект был фактически удален с сервера, а затем добавить его.  
  
## <a name="reloading-projects"></a>Перезагрузка проектов  
 Для функции поддержки перезагрузки вложенных проектов, необходимо реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> метод. В реализации `ReloadItem`, закрыть вложенные проекты и создайте их заново.  
  
 Обычно при перезагрузке проекта интегрированной среды разработки вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> и `M:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject(Microsoft.VisualStudio.Shell.Interop.IVsHierarchy,Microsoft.VisualStudio.Shell.Interop.IVsHierarchy)` события. Однако для вложенных проектов, которые будут удалены и загружаются в память, родительского проекта инициирует процесс, не интегрированной среды разработки. Поскольку в родительский проект, не порождает событий решения и интегрированной среды разработки не обладает информацией об инициализации процесса, не вызываются события.  
  
 Для обработки этого процесса, вызываемого проектом родительской `QueryInterface` на <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> интерфейс. `IVsFireSolutionEvents` содержит функции, которые сообщают интегрированной среды разработки для вызова `OnBeforeUnloadProject` событие, чтобы выгрузить вложенного проекта, а затем вызвать `OnAfterLoadProject` событий для перезагрузки тот же проект.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 [Проекты вложения](../../extensibility/internals/nesting-projects.md)
