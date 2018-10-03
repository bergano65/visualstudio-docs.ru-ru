---
title: Рекомендации по выгрузке и перезагрузке вложенных проектов | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4d932096d209d8e39b5d218ceb868453fa9a8a6f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47573253"
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>Рекомендации по выгрузке и перезагрузке вложенных проектов
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [вопросы выгрузка и перезагрузке вложенных проектов](https://docs.microsoft.com/visualstudio/extensibility/internals/considerations-for-unloading-and-reloading-nested-projects).  
  
При реализации типов вложенных проектов, необходимо выполнить дополнительные действия, когда Вы выгрузите, а затем перезагрузить проекты. Чтобы правильно уведомлять прослушивателей событий решения, нужно правильно повысить `OnBeforeUnloadProject` и `OnAfterLoadProject` события.  
  
 Одна из причин, необходимо изменить эти события таким образом, что делает не системы управления исходным кодом (SCC), чтобы удалить элементы с сервера, а затем добавьте на их обратно как что-то новое, если имеется `Get` операции SCC. В этом случае загружается новый файл из SCC, и вам придется выгружать и загружать файлы, если они отличаются. Вызовы SCC `ReloadItem`. Реализации этого вызова является удаление проекта и повторно создайте его заново, реализовав `IVsFireSolutionEvents` для вызова `OnBeforeUnloadProject` и `OnAfterLoadProject`. При выполнении этой реализации, SCC получает сведения проекта была временно удалена и снова добавить. Таким образом SCC не работают с проекта, как в том случае, если проект был фактически удален с сервера, а затем добавить его.  
  
## <a name="reloading-projects"></a>Перезагрузка проектов  
 Для функции поддержки перезагрузки вложенных проектов, необходимо реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> метод. В реализации `ReloadItem`, закрыть вложенные проекты и создайте их заново.  
  
 Обычно при перезагрузке проекта интегрированной среды разработки вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> и `M:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject(Microsoft.VisualStudio.Shell.Interop.IVsHierarchy,Microsoft.VisualStudio.Shell.Interop.IVsHierarchy)` события. Однако для вложенных проектов, которые будут удалены и загружаются в память, родительского проекта инициирует процесс, не интегрированной среды разработки. Поскольку в родительский проект, не порождает событий решения и интегрированной среды разработки не обладает информацией об инициализации процесса, не вызываются события.  
  
 Для обработки этого процесса, вызываемого проектом родительской `QueryInterface` на <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> интерфейс. `IVsFireSolutionEvents` содержит функции, которые сообщают интегрированной среды разработки для вызова `OnBeforeUnloadProject` событие, чтобы выгрузить вложенного проекта, а затем вызвать `OnAfterLoadProject` событий для перезагрузки тот же проект.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 [Проекты вложения](../../extensibility/internals/nesting-projects.md)

