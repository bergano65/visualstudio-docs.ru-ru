---
title: Объект конфигурации проекта | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project configurations, object
- objects, project configuration
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7385a5f7768a57fd1a3d9688df152fd60a1ea130
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="project-configuration-object"></a>Объект конфигурации проекта
Объект конфигурации проекта, который управляет Отображение сведений о конфигурации в пользовательском Интерфейсе.  
  
 ![Настройка проекта Visual Studio](../../extensibility/internals/media/vsprojectcfg.gif "vsProjectCfg")  
Страницы свойств конфигурации проекта  
  
 Поставщик конфигурации проекта управляет конфигурации проекта. Среда и другие пакеты, чтобы получить доступ к и получить сведения о конфигурации проекта, вызывать интерфейсы, присоединенные к объекту поставщик конфигурации проекта.  
  
> [!NOTE]
>  Невозможно создать или изменить файлы конфигурации решения программными средствами. Необходимо использовать `DTE.SolutionBuilder`. В разделе [конфигурации решения](../../extensibility/internals/solution-configuration.md) для получения дополнительной информации.  
  
 Чтобы опубликовать отображаемое имя для использования в конфигурации пользовательского интерфейса, должны реализовывать проекта <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A>. Среда вызывает метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, который возвращает список `IVsCfg` указатели, которые можно использовать для получения сведения о конфигурации и платформы будет отображаться в пользовательском Интерфейсе среды отображаемые имена. Активная конфигурация и платформа определяются конфигурацию проекта, хранимых в активной конфигурации решения. <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A> Метод может использоваться для получения конфигурации активного проекта.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> Объекта при необходимости могут быть реализованы в <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> объекта с <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper> объекта, чтобы можно было получить `IVsProjectCfg2` объекта, основанного на имя конфигурации проекта канонической.  
  
 Другой способ предоставления доступа к конфигурации проекта среды и других проектов — для проектов, чтобы обеспечить реализацию `IVsCfgProvider2::GetCfgs` метод для возврата одного или нескольких объектов конфигурации. Проекты могут также реализовывать <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>, который наследует от `IVsProjectCfg` и тем самым из `IVsCfg`, для предоставления сведений, относящихся к конфигурации. <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> поддерживает функции и платформы для Добавление, удаление и переименование конфигурации проекта.  
  
> [!NOTE]
>  Поскольку Visual Studio больше не ограничивается два типа конфигурации, не следует записывать код, который обрабатывает конфигураций с предположения о количестве конфигураций, а также он должен быть записан исходя из предположения, что проект, который имеет только один Конфигурация — это обязательно отладки или в розницу. Это делает использование <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A> устарел.  
  
 Вызов `QueryInterface` на объект, возвращаемый из`IVsGetCfgProvider::GetCfgProvider` извлекает `IVsCfgProvider2`. Если `IVsGetCfgProvider` не найден, вызвав `QueryInterface` на `IVsProject3` объекта проекта, доступ к поставщику объект конфигурации путем вызова `QueryInterface` в корневом объекте обозревателя иерархии для объекта, возвращаемого для `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)`, либо с помощью указатель на поставщик конфигурации, возвращаемые для `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)`.  
  
 `IVsProjectCfg2` в первую очередь обеспечивает доступ для построения, отладки и развертывания объектов управления и позволяет проекты свободу группы выходных данных. Методы `IVsProjectCfg` и `IVsProjectCfg2` можно использовать для реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> для управления процессом построения и <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> указатели для группы выходных данных конфигурации.  
  
 Проект должен возвращать одинаковое количество групп для каждой конфигурации, который он поддерживает, несмотря на то, что количество выходов, содержащихся в группе зависит от конфигурации для конфигурации. Группы должен также иметь те же сведения идентификатора (каноническое имя, отображаемое имя и сведения о группе) из конфигурации для конфигурации в рамках проекта. Дополнительные сведения см. в разделе [конфигурации проекта для вывода](../../extensibility/internals/project-configuration-for-output.md).  
  
 Чтобы включить отладку, должны реализовывать собственные конфигурации <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>. `IVsDebuggableProjectCfg` дополнительный интерфейс, реализуемый проекты, чтобы разрешить отладчику запустить конфигурацию и реализован в объекте конфигурации с `IVsCfg` и `IVsProjectCfg`. Окружение вызывает его, когда пользователь вручную запустить отладчик, нажав клавишу F5.  
  
 `ISpecifyPropertyPages` и `IDispatch` используются в сочетании с помощью страниц свойств для получения и отображения информации в зависимости от конфигурации для пользователя. Дополнительные сведения см. в разделе [страницы свойств](../../extensibility/internals/property-pages.md).  
  
## <a name="see-also"></a>См. также  
 [Управление параметрами конфигурации](../../extensibility/internals/managing-configuration-options.md)   
 [Настройка проекта для построения](../../extensibility/internals/project-configuration-for-building.md)   
 [Настройка проекта для выходных данных](../../extensibility/internals/project-configuration-for-output.md)   
 [Страницы свойств](../../extensibility/internals/property-pages.md)   
 [Конфигурация решения](../../extensibility/internals/solution-configuration.md)