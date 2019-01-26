---
title: Рекомендации по выгрузке и перезагрузке вложенных проектов | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b0b5738a5e8cf01466dd632797c3f92ffd135a44
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54942744"
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>Рекомендации по выгрузке и перезагрузке вложенных проектов

При реализации типов вложенных проектов, необходимо выполнить дополнительные действия, когда Вы выгрузите, а затем перезагрузить проекты. Чтобы правильно уведомлять прослушивателей событий решения, нужно правильно повысить `OnBeforeUnloadProject` и `OnAfterLoadProject` события.

Одна из причин для создания этих событий, — для управления исходным кодом (SCC). Вы не хотите SCC, чтобы удалить элементы с сервера, а затем добавьте их обратно в качестве *новый* при наличии `Get` операции SCC. В этом случае будет загрузить новый файл из SCC. Вам придется выгружать и загружать все файлы, в случае, если они отличаются.

Исходный код вызывает метод управления `ReloadItem`. Реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> интерфейс, необходимо вызвать `OnBeforeUnloadProject` и `OnAfterLoadProject` удалить проект и создать его повторно. При реализации интерфейса таким образом, SCC получает сведения проекта была временно удалена и снова добавить. Таким образом, не работает SCC проекта как, если проект был *фактически* удаляется и повторно добавить.

## <a name="reload-projects"></a>Перезагрузить проекты

Для функции поддержки перезагрузки вложенных проектов, необходимо реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> метод. В реализации `ReloadItem`, закрыть вложенные проекты и создайте их заново.

Обычно при перезагрузке проекта интегрированной среды разработки вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> события. Однако для вложенных проектов, которые будут удалены и загружаются в память, родительского проекта инициирует процесс, а не интегрированной среды разработки. Поскольку в родительский проект не вызывают события решения и интегрированной среды разработки не обладает информацией об инициализации процесса, не события.

Для обработки этого процесса, вызываемого проектом родительской `QueryInterface` на <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> интерфейс. `IVsFireSolutionEvents` содержит функции, которые сообщают интегрированной среды разработки для вызова `OnBeforeUnloadProject` событие, чтобы выгрузить вложенного проекта, а затем вызвать `OnAfterLoadProject` событий для перезагрузки тот же проект.

## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- [Проекты вложения](../../extensibility/internals/nesting-projects.md)