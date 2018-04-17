---
title: Рекомендации для выгрузки и загрузки вложенные проекты | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7f22575c4affa6e6a13ea80b32674a3e517202fb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>Рекомендации по выгрузка и перезагрузка проектов вложенные

При реализации проекта вложенные типы должны выполнения дополнительных действий при выгрузить и перезагрузить проекты. Правильно уведомляла прослушивателями событий решения, необходимо правильно повысить `OnBeforeUnloadProject` и `OnAfterLoadProject` события.

Для управления исходным кодом (SCC) — одна из причин для создания этих событий. Вы не хотите SCC, чтобы удалить элементы с сервера, а затем добавьте их обратно в качестве *новый* при наличии `Get` операции SCC. В этом случае новый файл загружается из SCC. Будет необходимо выгрузить и снова загрузить файлы в случае, если они отличаются.

Исходный код вызывает метод управления `ReloadItem`. Реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> интерфейс для вызова `OnBeforeUnloadProject` и `OnAfterLoadProject` удалить проект и создать его повторно. При реализации интерфейса таким образом, SCC получает сведения, что проект был временно удалить и снова добавить. Таким образом, не работает SCC проекта, если проект был *фактически* удален и повторно добавлен.

## <a name="reloading-projects"></a>Перезагрузка проектов

Для поддержки перезагрузке вложенных проектов, необходимо реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> метод. В реализации `ReloadItem`, закройте вложенных проектов и создайте их заново.

Обычно при перезагрузке проекта IDE вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> события. Однако для вложенных проектов, которые будут удалены и загружаются в память, родительский проект инициирует процесс, а не интегрированной среды разработки. Так как родительский проект не вызывает событий решения и интегрированной среды разработки не содержит сведений об инициализации процесса, не являются события.

Для обработки этого процесса вызовы родительский проект `QueryInterface` на <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> интерфейса. `IVsFireSolutionEvents` содержит функции, сообщающие интегрированной среды разработки для вызова `OnBeforeUnloadProject` событий для выгрузки вложенный проект и затем вызвать `OnAfterLoadProject` событий перезагрузить одного проекта.

## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- [Проекты вложения](../../extensibility/internals/nesting-projects.md)