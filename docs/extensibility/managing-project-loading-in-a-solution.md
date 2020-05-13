---
title: Управление загрузкой проекта в решении (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 21cd5e7e557e795db49aea7a14e8e4cc7caa0422
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702730"
---
# <a name="manage-project-loading-in-a-solution"></a>Управление загрузкой проекта в решении
Решения Visual Studio могут содержать большое количество проектов. Поведение Visual Studio по умолчанию заключается в загрузке всех проектов в решение на момент открытия решения и не позволить пользователю получить доступ к любому из проектов до тех пор, пока все они не закончат загрузку. Когда процесс загрузки проекта длится более двух минут, отображается панель прогресса, показывающая количество загруженных проектов и общее количество проектов. Пользователь может разгрузить проекты во время работы в решении с несколькими проектами, но эта процедура имеет некоторые недостатки: разгруженные проекты не строятся как часть команды Rebuild Solution, а описания типов и участников закрытых проектов IntelliSense не отображаются.

 Разработчики могут сократить время загрузки решения и управлять поведением загрузки проекта, создав диспетчера нагрузки. Менеджер загрузки решения может убедиться, что проекты загружаются перед началом фоновой сборки, отложить фоновую загрузку до завершения других фоновых задач и выполнить другие задачи по управлению нагрузкой проекта.

## <a name="create-a-solution-load-manager"></a>Создание менеджера нагрузки на решение
 Разработчики могут создать диспетчера <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> загрузки решений, внедрив и посоветовав Visual Studio, что менеджер загрузки решения активен.

### <a name="activate-a-solution-load-manager"></a>Активировать менеджера нагрузки решения
 Visual Studio позволяет только один менеджер нагрузки решения в данный момент времени, так что вы должны сообщить Visual Studio, когда вы хотите, чтобы активировать ваш менеджер нагрузки решения. Если менеджер загрузки второго решения активируется позже, менеджер нагрузки решения будет отключен.

 Вы должны <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> получить услугу и установить [__VSPROPID4. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) имущество:

```csharp
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;
object objLoadMgr = this;   //the class that implements IVsSolutionManager
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);
```

 Метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A> вызывается либо при закрытии Visual Studio, либо когда другой пакет стал менеджером загрузки активного решения, позвонив <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> в [__VSPROPID4. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) собственность.

#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>Стратегии для различных видов менеджера нагрузки решения
 Менеджеры загрузки решений можно реализовать по-разному, в зависимости от типов решений, которыми они предназначены для управления.

 Если диспетчер загрузки решения предназначен для управления загрузкой решения в целом, он может быть реализован как часть VSPackage. Пакет должен быть установлен для автоматической загрузки путем <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid>добавления на VSPackage со значением. Менеджер загрузки решения может быть <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> активирован в методе.

> [!NOTE]
> Для получения дополнительной информации о пакетах автоматической [загрузки см.](../extensibility/loading-vspackages.md)

 Поскольку Visual Studio распознает только последний менеджер загрузки решения, который должен быть активирован, менеджеры нагрузок общего решения всегда должны определить, есть ли существующий менеджер нагрузки, прежде чем активировать себя. При `GetProperty()` вызове службы решения для [__VSPROPID4. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) `null`возвращается, нет активного менеджера загрузки решения. Если он не возвращается недействительным, проверьте, является ли объект таким же, как ваш менеджер нагрузки решения.

 Если диспетчер загрузки решения предназначен для управления только несколькими типами решений, VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>может подписаться на <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> события загрузки решения (по вызову) и использовать обработчик событий для активации менеджера нагрузки решения.

 Если диспетчер загрузки решения предназначен для управления только конкретными решениями, информация об <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> активации может сохраняться как часть файла решения, вызывая раздел предварительного решения.

 Конкретные менеджеры нагрузки решения <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> должны деактивировать себя в обработчике событий, чтобы не властвовать с другими менеджерами нагрузки решения.

 Если менеджер нагрузки решения нужен только для сохранения глобальных свойств нагрузки проекта (например, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> свойства, установленные на странице Options), можно активировать диспетчернагрузки решения в обработчике событий, упорствовать в настройках решения, а затем отключить диспетчер нагрузки решения.

## <a name="handle-solution-load-events"></a>Обработка событий загрузки решения
 Чтобы подписаться на события <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> загрузки решения, позвоните при активации менеджера загрузки решения. При реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents>можно реагировать на события, связанные с различными свойствами загрузки проекта.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: Это событие происходит перед открытием решения.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: Это событие срабатывало после полной загрузки решения, но до того, как снова начинается загрузка фонового проекта.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: Это событие происходит после того, как решение изначально полностью загружено, независимо от того, есть ли менеджер нагрузки решения. Он также выстрелил после фоновой нагрузки или нагрузки спроса всякий раз, когда решение становится полностью загруженным. В то же <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> время, активируется.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: Это событие происходит перед загрузкой проекта (или проектов). Чтобы обеспечить завершение других фоновых процессов `pfShouldDelayLoadToNextIdle` до загрузки проектов, установите **истину.**

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: Это событие происходит при загрузке партии проектов. Если `fIsBackgroundIdleBatch` это так, то проекты должны быть загружены в фоновом режиме; если `fIsBackgroundIdleBatch` это нетак, проекты должны быть загружены синхронно в результате запроса пользователя, например, если пользователь расширяет отложенный проект в Solution Explorer. Вы можете справиться с этим событием, чтобы <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>сделать дорогую работу, которая в противном случае необходимо будет сделать в .

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: Это событие вырабатывалось после загрузки партии проектов.

## <a name="detect-and-manage-solution-and-project-loading"></a>Обнаружение и управление загрузкой решений и проектов
 Для определения состояния нагрузки проектов и <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> решений звоните со следующими значениями:

- [__VSPROPID4. VSPROPID_IsSolutionFullyLoaded](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsSolutionFullyLoaded>) `var` : `true` возвращается, если решение и все `false`его проекты загружены, в противном случае.

- [__VSPROPID4. VSPROPID_IsInBackgroundIdleLoadProjectBatch](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInBackgroundIdleLoadProjectBatch>) `var` : `true` возвращается, если партия проектов в настоящее время загружается в фоновом режиме, в противном случае `false`.

- [__VSPROPID4. VSPROPID_IsInSyncDemandLoadProjectBatch](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInSyncDemandLoadProjectBatch>) `var` : `true` возвращается, если партия проектов в настоящее время загружается синхронно в результате команды пользователя или другой явной нагрузки, в противном случае. `false`

- [__VSPROPID2. VSPROPID_IsSolutionClosing](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2.VSPROPID_IsSolutionClosing>) `var` : `true` возвращается, если решение `false`в настоящее время закрывается, в противном случае .

- [__VSPROPID. VSPROPID_IsSolutionOpening](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID.VSPROPID_IsSolutionOpening>) `var` : `true` возвращается, если решение `false`в настоящее время открывается, в противном случае .

Вы также можете гарантировать, что проекты и решения загружаются, вызывая один из следующих методов:

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: вызов этого метода заставляет проекты в решении для загрузки до возвращения метода.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: вызов этого метода `guidProject` заставляет проекты загружаться до возвращения метода.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: вызов этого метода `guidProjectID` заставляет проект загружаться до возвращения метода.
