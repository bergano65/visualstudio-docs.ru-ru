---
title: Выгрузка и повторная загрузка вложенных проектов
description: Дополнительные действия, которые необходимо выполнить при выгрузке и перезагрузке вложенных проектов в Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ed91ac56929682205937122a4521ad7233af675f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884654"
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>Рекомендации по выгрузке и перезагрузке вложенных проектов

При реализации вложенных типов проектов необходимо выполнить дополнительные действия при выгрузке и перезагрузке проектов. Чтобы правильно уведомить прослушиватели о событиях решения, необходимо правильно вызвать `OnBeforeUnloadProject` `OnAfterLoadProject` события и.

Одной из причин для вызова этих событий является управление исходным кодом (SCC). Вы не хотите, чтобы SCC удалили элементы с сервера, а затем добавили *их вновь, если в* SCC имеется `Get` операция. В этом случае новый файл будет загружен из SCC. Вам пришлось бы выгружать и перезагружать все файлы на случай, если они отличаются.

Вызовы системы управления исходным кодом `ReloadItem` . Реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> интерфейс для вызова `OnBeforeUnloadProject` и `OnAfterLoadProject` удаления проекта и его повторного создания. При таком способе реализации интерфейса SCC уведомляет о том, что проект был временно удален и добавлен снова. Таким образом, SCC не работает с проектом, как если бы проект был *фактически* удален и добавлен повторно.

## <a name="reload-projects"></a>Перезагрузить проекты

Для поддержки перезагрузки вложенных проектов необходимо реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> метод. В реализации `ReloadItem` вы закрываете вложенные проекты, а затем создаете их повторно.

Как правило, при повторной загрузке проекта интегрированная среда разработки создает <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> события и. Однако для удаленных и перезагруженных вложенных проектов родительский проект запускает процесс, а не интегрированную среду разработки. Поскольку родительский проект не создает события решения, и в интегрированной среде разработки нет сведений о инициализации процесса, события не вызываются.

Для обработки этого процесса родительский проект вызывает `QueryInterface` <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> интерфейс. `IVsFireSolutionEvents` содержит функции, которые сообщают интегрированной среде разработки о необходимости вызова `OnBeforeUnloadProject` события для выгрузки вложенного проекта, а затем вызывают `OnAfterLoadProject` событие для повторной загрузки того же проекта.

## <a name="see-also"></a>См. также раздел

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- [Вложенные проекты](../../extensibility/internals/nesting-projects.md)
