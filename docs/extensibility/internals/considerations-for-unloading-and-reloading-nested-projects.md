---
title: Рассмотрение вопросов разгрузки и перегрузки nested проектов (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2ab705953eea1fcac99883bb4f88c0e95eced108
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709288"
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>Рассмотрение вопросов разгрузки и перегрузки вложенных проектов

При реализации вложенных типов проектов необходимо выполнить дополнительные действия при разгрузке и перезагрузке проектов. Чтобы правильно уведомить слушателей о событиях `OnBeforeUnloadProject` решения, необходимо правильно поднять `OnAfterLoadProject` и события.

Одной из причин для повышения этих событий является контроль исходного кода (SCC). Вы не хотите, чтобы SCC удалял элементы с сервера, `Get` а затем добавлял их обратно в *качестве новых,* если есть операция от SCC. В этом случае новый файл будет загружен из SCC. Вам придется выгрузить и перезагрузить все файлы в случае, если они отличаются.

Вызовы `ReloadItem`управления исходного кода . Реализуйте `OnBeforeUnloadProject` интерфейс `OnAfterLoadProject` для <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> вызова и удаления проекта и воссоздайте его. При реализации интерфейса таким образом, SCC сообщается, что проект был временно удален и добавлен снова. Таким образом, SCC не работает на проекте, как если бы проект был *фактически* удален и повторно добавлен.

## <a name="reload-projects"></a>Перезагрузить проекты

Для поддержки перезагрузки вложенных проектов, вы реализуете <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> метод. В вашей `ReloadItem`реализации, вы закрываете вложенные проекты, а затем воссоздать их.

Обычно при перезагрузке проекта IDE поднимает <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> и события. Однако для вложенных проектов, которые удаляются и перезагружаются, родительский проект инициирует процесс, а не IDE. Поскольку родительский проект не поднимает события решения, а IDE не располагает информацией о инициализации процесса, события не поднимаются.

Чтобы справиться с этим `QueryInterface` процессом, родительский проект вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> интерфейс. `IVsFireSolutionEvents`имеет функции, которые говорят `OnBeforeUnloadProject` IDE поднять событие для разгрузки `OnAfterLoadProject` вложенного проекта, а затем поднять событие для перезагрузки того же проекта.

## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- [Проекты гнезда](../../extensibility/internals/nesting-projects.md)
