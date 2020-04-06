---
title: Объект конфигурации проекта (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, object
- objects, project configuration
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 001509b56e3bac6a8fd585eb0efe0bd57018acea
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706653"
---
# <a name="project-configuration-object"></a>Объект конфигурации проекта
Объект конфигурации проекта управляет отображением информации о конфигурации в uI.

 ![Конфигурация проекта Visual Studio](../../extensibility/internals/media/vsprojectcfg.gif "vsПроектCfg") Страницы свойств конфигурации проекта

 Поставщик конфигурации проекта управляет конфигурациями проекта. Среда и другие пакеты, чтобы получить доступ к конфигурациям проекта и получить ее, вызовуйте интерфейсы, прикрепленные к объекту поставщика конфигурации project.

> [!NOTE]
> Вы не можете создавать или отсчитывать файлы конфигурации решений программно. Для этого необходимо использовать `DTE.SolutionBuilder`. Дополнительную информацию можно найти в [настройках решений.](../../extensibility/internals/solution-configuration.md)

 Чтобы опубликовать имя дисплея, которое будет использоваться <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A>в мине конфигурации, проект должен реализоваться. Среда вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, который возвращает `IVsCfg` список указателей, которые можно использовать для получения имен отображения для информации о конфигурации и платформе, которые будут перечислены в uI среды. Активная конфигурация и платформа определяются конфигурацией проекта, хранящейся в конфигурации активного решения. Метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A> может быть использован для получения активной конфигурации проекта.

 Объект <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> может быть дополнительно реализован <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> на <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper> объекте с объектом, `IVsProjectCfg2` чтобы позволить вам получить объект на основе канонического названия конфигурации проекта.

 Другой способ обеспечить среду и другие проекты с доступом к `IVsCfgProvider2::GetCfgs` конфигурациям проектов для проектов, чтобы обеспечить реализацию метода, чтобы вернуть один или несколько объектов конфигурации. Проекты могут <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>также осуществлять , `IVsProjectCfg` который наследует от и, таким образом, от `IVsCfg`, чтобы предоставить конфигурацию конкретной информации. <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>поддерживает платформы и функциональность для добавления, удаляния и переименования конфигураций проектов.

> [!NOTE]
> Поскольку Visual Studio больше не ограничивается двумя типами конфигураций, код, который обрабатывает конфигурации, не должен быть написан с предположениями о количестве конфигураций, а также должен быть написан с предположением, что проект, который имеет только одну конфигурацию, обязательно либо debug, либо Retail. Это делает использование <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A> и устарели.

 Вызов `QueryInterface` на объект,`IVsGetCfgProvider::GetCfgProvider` возвращенный из извлечений. `IVsCfgProvider2` Если `IVsGetCfgProvider` не найдено, `QueryInterface` вызывая `IVsProject3` объект проекта, можно получить доступ `QueryInterface` к объекту поставщика конфигурации, `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)`вызывая объект корневого браузера `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)`иерархии для объекта, возвращенного для, или через указатель на реверс-провайдер конфигурации, возвращенный для .

 `IVsProjectCfg2`в первую очередь обеспечивает доступ к объектам управления сборкой, отладке и развертыванием и позволяет проектам свободно группировать выходы. Методы и `IVsProjectCfg` `IVsProjectCfg2` могут быть использованы для реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> для управления процессом сборки, а также указатели для групп вывода конфигурации.

 Проект должен возвращать одинаковое количество групп для каждой конфигурации, которое он поддерживает, даже если количество выходов, содержащихся в группе, может варьироваться от конфигурации к конфигурации. Группы также должны иметь одинаковую идентификационную информацию (каноническое имя, имя дисплея и групповую информацию) от конфигурации к конфигурации в проекте. Для получения дополнительной информации [см.](../../extensibility/internals/project-configuration-for-output.md)

 Для включения отладки необходимо <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>реализовать конфигурации. `IVsDebuggableProjectCfg`— это дополнительный интерфейс, реализованный проектами, позволяющий отладчику `IVsCfg` запускать конфигурацию и реализованный на объекте конфигурации с и `IVsProjectCfg`. Среда вызывает его, когда пользователь выбирает, чтобы начать отладчик, нажав F5.

 `ISpecifyPropertyPages`и `IDispatch` используются в сочетании со страницами свойств для извлечения и отображения информации, зависящей от конфигурации, для пользователя. Для получения дополнительной информации смотрите [страницы свойств](../../extensibility/internals/property-pages.md).

## <a name="see-also"></a>См. также
- [Управление параметрами конфигурации](../../extensibility/internals/managing-configuration-options.md)
- [Конфигурация проекта для сборки](../../extensibility/internals/project-configuration-for-building.md)
- [Конфигурация проекта для вывода](../../extensibility/internals/project-configuration-for-output.md)
- [Страницы свойств](../../extensibility/internals/property-pages.md)
- [Конфигурация решения](../../extensibility/internals/solution-configuration.md)
