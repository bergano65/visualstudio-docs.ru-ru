---
title: Объект конфигурации проекта | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, object
- objects, project configuration
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 682df39774d3f58ca4d4d0df560b2d900b8f6c9c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55006883"
---
# <a name="project-configuration-object"></a>Объект конфигурации проекта
Объект конфигурации проекта управляет отображением сведений о конфигурации в пользовательском Интерфейсе.  
  
 ![Конфигурация проекта Visual Studio](../../extensibility/internals/media/vsprojectcfg.gif "vsProjectCfg")  
Страницы свойств конфигурации проекта  
  
 Поставщик конфигурации проекта управляет конфигурации проекта. Среда и другие пакеты, для получения доступа к и получения сведений о конфигурации проекта, вызывают интерфейсы, присоединенный к объекту поставщика конфигурации проекта.  
  
> [!NOTE]
>  Не удается создать или изменить файлы конфигурации решения программным способом. Необходимо использовать `DTE.SolutionBuilder`. См. в разделе [конфигурации решения](../../extensibility/internals/solution-configuration.md) Дополнительные сведения.  
  
 Чтобы опубликовать отображаемое имя для использования в конфигурации пользовательского интерфейса, следует реализовать проекта <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A>. Среда вызывает метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, который возвращает список `IVsCfg` указатели, которые можно использовать для получения отображаемые имена сведения конфигурации и платформы, которые будут указаны в пользовательском Интерфейсе среды. Активная конфигурация и платформа определяются конфигурации проекта, хранящиеся в активной конфигурации решения. <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A> Метод может использоваться для получения конфигурации активного проекта.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> Объекта при необходимости может быть реализован на <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> со <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper> объекта, чтобы можно было получить `IVsProjectCfg2` на имя конфигурации проекта каноническую основе.  
  
 Еще один способ предоставления доступа к конфигурации проектов среды и других проектов — для проектов, чтобы предоставить реализацию `IVsCfgProvider2::GetCfgs` метод для возврата одного или нескольких объектов конфигурации. Проекты могут также реализовывать <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>, который наследует от `IVsProjectCfg` и тем самым из `IVsCfg`, чтобы предоставить сведения, относящиеся к конфигурации. <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> поддерживает платформы и функциональные возможности для Добавление, удаление и переименование конфигурации проекта.  
  
> [!NOTE]
>  Так, как Visual Studio больше не ограничены два типа конфигурации, не следует записывать код, обрабатывающий конфигураций с предположения о количестве конфигураций, и он должен быть записан в предположении, что проект, который содержит только один Конфигурация может быть Debug или Retail. Это делает использование <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A> устаревшим.  
  
 Вызов `QueryInterface` на объект, возвращенный из`IVsGetCfgProvider::GetCfgProvider` извлекает `IVsCfgProvider2`. Если `IVsGetCfgProvider` не найден, вызвав `QueryInterface` на `IVsProject3` объекта проекта, можно получить доступ к объект поставщика настроек путем вызова `QueryInterface` на иерархии корневой объект браузера для объекта, возвращаемого для `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)`, либо с помощью указатель на поставщик конфигурации, возвращаемые для `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)`.  
  
 `IVsProjectCfg2` в первую очередь обеспечивает доступ для построения, отладки и развертывания объектов управления и позволяет проектов возможность группировать вывод. Методы `IVsProjectCfg` и `IVsProjectCfg2` может использоваться для реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> для управления процессом построения, и <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> указатели для групп вывода конфигурации.  
  
 Проект должен возвращать одинаковое количество групп для каждой конфигурации, которую она поддерживает, несмотря на то, что количество выходов, содержащихся в группе может отличаться от конфигурации для конфигурации. Группы должен также иметь же сведения идентификатора (каноническое имя, отображаемое имя и сведения о группе) из конфигурации для конфигурации в рамках проекта. Дополнительные сведения см. в разделе [конфигурация проекта для вывода](../../extensibility/internals/project-configuration-for-output.md).  
  
 Чтобы включить отладку, необходимо реализовать конфигурации <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>. `IVsDebuggableProjectCfg` дополнительный интерфейс, реализованный проектами, чтобы отладчик для запуска в конфигурации и реализуется в объекте конфигурации с `IVsCfg` и `IVsProjectCfg`. Среда вызывает его, когда пользователь вручную запустить отладчик, нажав клавишу F5.  
  
 `ISpecifyPropertyPages` и `IDispatch` используются вместе с помощью страниц свойств для извлечения и отображения данных, зависящих от конфигурации для пользователя. Дополнительные сведения см. в разделе [страницы свойств](../../extensibility/internals/property-pages.md).  
  
## <a name="see-also"></a>См. также  
 [Управление параметрами конфигурации](../../extensibility/internals/managing-configuration-options.md)   
 [Конфигурация проекта для сборки](../../extensibility/internals/project-configuration-for-building.md)   
 [Конфигурация проекта для вывода](../../extensibility/internals/project-configuration-for-output.md)   
 [Страницы свойств](../../extensibility/internals/property-pages.md)   
 [Конфигурация решения](../../extensibility/internals/solution-configuration.md)