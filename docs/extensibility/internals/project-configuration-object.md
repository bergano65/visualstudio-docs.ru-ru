---
title: "Объект конфигурации проекта | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project configurations, object
- objects, project configuration
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 0518e4844dd7fa7710935f742bf44943a5ef945d
ms.lasthandoff: 02/22/2017

---
# <a name="project-configuration-object"></a>Объект конфигурации проекта
Объект конфигурации проекта управляет Отображение сведений о конфигурации в пользовательском Интерфейсе.  
  
 ![Конфигурация проекта Visual Studio](~/extensibility/internals/media/vsprojectcfg.gif "vsProjectCfg")  
Страницы свойств конфигурации проекта  
  
 Поставщик конфигурации проекта управляет конфигурации проекта. Среда и другие пакеты, чтобы получить доступ и получить сведения о конфигурации проекта, вызывают интерфейсы, присоединенные к объекту поставщик конфигурации проекта.  
  
> [!NOTE]
>  Не удается создать или программно изменить файлы конфигурации решения. Необходимо использовать `DTE.SolutionBuilder`. В разделе [конфигурация решения](../../extensibility/internals/solution-configuration.md) подробнее.  
  
 Чтобы опубликовать отображаемое имя для использования в пользовательский Интерфейс настройки, проект следует реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A> Среда вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, который возвращает список `IVsCfg` указатели, которые можно использовать для получения сведения о конфигурации и платформы перечислены в пользовательском Интерфейсе среды отображаемые имена.</xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A> Активная конфигурация и платформа определяются конфигурации проекта, хранящиеся в активной конфигурации решения. <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A>Метод может использоваться для извлечения конфигурации активного проекта.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>Объекта при необходимости могут быть реализованы в <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>объекта с <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper>объекта, чтобы вы могли получить `IVsProjectCfg2` в соответствии с имя конфигурации проекта каноническим.</xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper> </xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> </xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>  
  
 Другой способ предоставления доступа к конфигурации проекта среды и других проектов — для проектов предоставить реализацию `IVsCfgProvider2::GetCfgs` для возврата одного или нескольких объектов конфигурации. Проекты могут также реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>, который наследует от `IVsProjectCfg` и тем самым из `IVsCfg`, чтобы предоставить сведения о конфигурации.</xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>поддерживает функции и платформы для Добавление, удаление и переименование конфигурации проекта.</xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>  
  
> [!NOTE]
>  Поскольку Visual Studio больше не ограничен двумя типами конфигурации, не следует записывать код, который обрабатывает конфигураций с предположений о количестве конфигураций, а также должны его записываться предположении, что обязательно является проекта, который содержит только одну конфигурацию отладки или в розницу. Это позволяет использовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A>и <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A>устарело.</xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A>  
  
 Вызов `QueryInterface` на объект, возвращенный из`IVsGetCfgProvider::GetCfgProvider` извлекает `IVsCfgProvider2`. Если `IVsGetCfgProvider` не найден, вызвав `QueryInterface` на `IVsProject3` объекта проекта, доступ к поставщику объект конфигурации путем вызова `QueryInterface` на корневой объект браузера иерархии для объекта, возвращаемого для `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)`, или через указатель на поставщик конфигурации, возвращаемые для `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)`.  
  
 `IVsProjectCfg2`в первую очередь обеспечивает доступ для построения, отладки и развертывания объектов управления и позволяет свобода группы выходных данных проекта. Методы `IVsProjectCfg` и `IVsProjectCfg2` может использоваться для реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>для управления процессом построения и <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup>указатели для групп выходные данные конфигурации.</xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> </xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>  
  
 Проект должен возвращать одинаковое количество групп для каждой конфигурации, которые его поддерживают, несмотря на то, что количество выходов, содержащихся в группе зависит от конфигурации для конфигурации. Группы должен быть того же сведения идентификатора (каноническое имя, отображаемое имя и сведения о группе) с конфигурацией в рамках проекта. Дополнительные сведения см. в разделе [конфигурации проекта для вывода](../../extensibility/internals/project-configuration-for-output.md).  
  
 Чтобы включить отладку, настройки следует реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> `IVsDebuggableProjectCfg`Необязательный интерфейс, реализуемый проектов, чтобы разрешить отладчику запустить конфигурацию и реализован в объекте конфигурации с `IVsCfg` и `IVsProjectCfg`. Среда вызывает его, когда пользователь вручную запустить отладчик, нажав клавишу F5.  
  
 `ISpecifyPropertyPages`и `IDispatch` используются в сочетании с помощью страниц свойств для извлечения и отображения данных, зависящих от конфигурации для пользователя. Дополнительные сведения см. в разделе [страницы свойств](../../extensibility/internals/property-pages.md).  
  
## <a name="see-also"></a>См. также  
 [Управление параметрами конфигурации](../../extensibility/internals/managing-configuration-options.md)   
 [Настройка проекта для построения](../../extensibility/internals/project-configuration-for-building.md)   
 [Настройка проекта для вывода](../../extensibility/internals/project-configuration-for-output.md)   
 [Страницы свойств](../../extensibility/internals/property-pages.md)   
 [Конфигурация решения](../../extensibility/internals/solution-configuration.md)
