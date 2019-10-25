---
title: Объект конфигурации проекта | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, object
- objects, project configuration
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e3321b70b51d194c67f1deee8ed33e240762b16b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725838"
---
# <a name="project-configuration-object"></a>Объект конфигурации проекта
Объект конфигурации проекта управляет отображением сведений о конфигурации в пользовательском интерфейсе.

 ![Конфигурация проекта Visual Studio](../../extensibility/internals/media/vsprojectcfg.gif "вспрожекткфг") Страницы свойств конфигурации проекта

 Поставщик конфигурации проекта управляет конфигурациями проекта. Среда и другие пакеты для получения доступа к конфигурациям проекта и получения сведений о них вызывают интерфейсы, присоединенные к объекту поставщика конфигурации проекта.

> [!NOTE]
> Вы не можете создавать или изменять файлы конфигурации решения программным способом. Необходимо использовать `DTE.SolutionBuilder`. Дополнительные сведения см. в разделе [Конфигурация решения](../../extensibility/internals/solution-configuration.md) .

 Чтобы опубликовать отображаемое имя, которое будет использоваться в пользовательском интерфейсе конфигурации, проект должен реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A>. Среда вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, который возвращает список указателей `IVsCfg`, которые можно использовать для получения отображаемых имен конфигурации и сведений о платформе, которые должны быть перечислены в пользовательском интерфейсе окружения. Активная конфигурация и платформа определяются конфигурацией проекта, хранящейся в конфигурации активного решения. Метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A> можно использовать для получения активной конфигурации проекта.

 Объект <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> можно дополнительно реализовать в объекте <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> с объектом <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper>, чтобы получить объект `IVsProjectCfg2` на основе канонического имени конфигурации проекта.

 Другим способом предоставления среды и других проектов с доступом к конфигурациям проектов является использование проектов для предоставления реализации метода `IVsCfgProvider2::GetCfgs`, возвращающего один или несколько объектов конфигурации. Проекты также могут реализовывать <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>, которые наследуют от `IVsProjectCfg` и, таким образом, от `IVsCfg` для предоставления сведений о конфигурации. <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> поддерживает платформы и функциональные возможности для добавления, удаления и переименования конфигураций проекта.

> [!NOTE]
> Поскольку Visual Studio больше не ограничена двумя типами конфигураций, код, который обрабатывает конфигурации, не должен быть написан с предположения о количестве конфигураций, а также не должен быть написан с предположением, что проект, имеющий только один конфигурация должна быть как отладочной, так и розничной. Это делает использование <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A> устаревшим.

 Вызов `QueryInterface` для объекта, возвращенного из `IVsGetCfgProvider::GetCfgProvider`, извлекает `IVsCfgProvider2`. Если `IVsGetCfgProvider` не удается найти с помощью вызова `QueryInterface` для объекта `IVsProject3` проекта, можно получить доступ к объекту поставщика конфигурации, вызвав `QueryInterface` в корневом объекте браузера иерархии для объекта, возвращаемого для `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)`, или с помощью указателя на конфигурацию. поставщик, возвращенный для `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)`.

 `IVsProjectCfg2` в основном предоставляет доступ к объектам сборки, отладки и управления развертыванием, а также позволяет проектам свободно группировать выходные данные. Методы `IVsProjectCfg` и `IVsProjectCfg2` можно использовать для реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> для управления процессом сборки и <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> указателей для выходных групп конфигурации.

 Проект должен возвращать одинаковое количество групп для каждой поддерживаемой конфигурации, даже если количество выходов, содержащихся в группе, может отличаться от конфигурации к конфигурации. Группы также должны иметь одинаковые сведения об идентификаторе (каноническое имя, отображаемое имя и сведения о группе) из конфигурации в пределах проекта. Дополнительные сведения см. в разделе [Конфигурация проекта для выходных данных](../../extensibility/internals/project-configuration-for-output.md).

 Чтобы включить отладку, в конфигурациях должны быть реализованы <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>. `IVsDebuggableProjectCfg` — это необязательный интерфейс, реализуемый проектами, чтобы позволить отладчику запустить конфигурацию и реализовать его в объекте конфигурации с `IVsCfg` и `IVsProjectCfg`. Среда вызывает ее, когда пользователь выбирает, чтобы запустить отладчик, нажав клавишу F5.

 `ISpecifyPropertyPages` и `IDispatch` используются в сочетании со страницами свойств для получения и просмотра сведений, зависящих от конфигурации, для пользователя. Дополнительные сведения см. в разделе [страницы свойств](../../extensibility/internals/property-pages.md).

## <a name="see-also"></a>См. также
- [Управление параметрами конфигурации](../../extensibility/internals/managing-configuration-options.md)
- [Конфигурация проекта для сборки](../../extensibility/internals/project-configuration-for-building.md)
- [Конфигурация проекта для вывода](../../extensibility/internals/project-configuration-for-output.md)
- [Страницы свойств](../../extensibility/internals/property-pages.md)
- [Конфигурация решения](../../extensibility/internals/solution-configuration.md)