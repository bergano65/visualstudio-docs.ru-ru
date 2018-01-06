---
title: "Проект подтипы конструктора | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: project subtypes, design
ms.assetid: 405488bb-1362-40ed-b0f1-04a57fc98c56
caps.latest.revision: "32"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 126bee146d1f53233db3c14672f80da4c0d60e9e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="project-subtypes-design"></a>Подтипы конструктора проектов
Подтипы проекта позволяют пакеты VSPackage расширяют проектами с помощью Microsoft Build Engine (MSBuild). Использование статистической обработки позволяет повторно использовать большую часть реализации в системе проектов управляемого ядра [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , но по-прежнему настройки поведения для того или иного сценария.  
  
 Следующие разделы подробно описаны основные принципы проектирования и реализации подтипы проекта.  
  
-   Разработка подтип проекта.  
  
-   Многоуровневые статистической обработки.  
  
-   Поддержка интерфейсов.  
  
## <a name="project-subtype-design"></a>Подтип конструктора проектов  
 Инициализация подтипом проекта достигается за счет статистическая обработка главный <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> объектов. Объединение позволяет подтипом проекта для переопределения или изменения большинство возможностей из базового проекта. Подтипы проекта получает первый возможность обрабатывать с помощью свойства <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>, команд с использованием <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>и проект элемента управления с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>. Также можно расширить подтипы проекта:  
  
-   Объекты конфигурации проекта.  
  
-   Объекты, зависящие от конфигурации.  
  
-   Обзор зависят от конфигурации объектов.  
  
-   Объекты автоматизации проекта.  
  
-   Свойства автоматизации коллекциях.  
  
 Дополнительные сведения о расширяемости подтипов проекта, см. в разделе [свойства и методы расширенной подтипов проекта,](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md).  
  
##### <a name="policy-files"></a>Файлы политики  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Среда предоставляет пример расширения условий базовой системы проектов с подтипом проекта в своей реализации файлов политики. Файл политики позволяет формировать из [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] среды, управляя функциональные возможности, включая обозреватель решений, **добавить проект** диалоговом **Добавление нового элемента** диалоговое окно и  **Свойства** диалоговое окно. Подтип политики переопределяет и расширяет эти функции через <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg>, `IOleCommandTarget` и <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> реализации.  
  
##### <a name="aggregation-mechanism"></a>Механизм статистической обработки  
 Механизм статистической обработки подтип проекта среда поддерживает несколько уровней статистической обработки, что позволяет дополнительно подтип, должны быть реализованы дополнительные flavoring интерфейсам проекта. Кроме того, подтипа вспомогательные объекты проекта, такие как <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>, позволяют использовать несколько уровней слоев. В соответствии с ограничениями COM и COM правила статистической обработки, подтипов проекта и базовый проектов необходимо запрограммировать совместно для включения внутреннее подтип или базового проекта правильно участвовать в делегировании вызовы методов и управление счетчики ссылок . То есть проекте, которые должны быть статистически вычислена должен быть запрограммированы для поддержки статистической обработки.  
  
 На следующем рисунке схематически агрегата подтип многоуровневого проекта.  
  
 ![График Visual Studio multilevel projectflavor](../../extensibility/internals/media/vs_multilevelprojectflavor.gif "VS_MultilevelProjectFlavor")  
Подтип многоуровневой проекта  
  
 Является агрегатом подтип многоуровневого проекта состоит из трех уровней, базовый проект, который является статистическая обработка проводится путем подтипом проекта, то затем агрегируются с подтипом проекта Дополнительно. Рисунок рассматриваются некоторые вспомогательные интерфейсов, предоставляемых в составе [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] архитектура подтип проекта.  
  
##### <a name="deployment-mechanisms"></a>Механизмы развертывания  
 Из нескольких условий базовой системы проектов функциональные возможности расширены за счет подтипом проекта — это механизмы развертывания. Подтип проекта влияет механизмы развертывания путем реализации интерфейсов конфигурации (например, <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>), получаются путем вызова QueryInterface для <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>. В сценарии, где подтипом проекта и подтипом проекта Дополнительно добавьте другую конфигурацию реализации, вызывает базовый проект `QueryInterface` подтипов Дополнительно проекта `IUnknown`. Если подтипом внутреннего проекта содержит реализации конфигурации, запрашивающее базового проекта, подтипом проекта дополнительно делегирует реализацию, предоставляемую подтип внутреннего проекта. В качестве механизма для сохранения состояния уровень статистическая обработка, реализации всех уровней подтипов проекта <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> для сохранения без построения связанные XML-данных в файлы проекта. Дополнительные сведения см. в разделе [сохранение данных в файле проекта MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md). <xref:EnvDTE80.IInternalExtenderProvider>реализуется как механизм для извлечения из подтипов проекта автоматизированным расширителям.  
  
 Ниже рассматриваются реализация расширителя автоматизации, объект обзора конфигурации проекта в частности, использовать подтипов проекта, для расширения условий базовой системы проектов.  
  
 ![График авто расширения проекта Flavor VS](../../extensibility/internals/media/vs_projectflavorautoextender.gif "VS_ProjectFlavorAutoExtender")  
Автоматизированного расширителя подтип проекта.  
  
 Подтипы проекта можно расширить условий базовой системы проектов, расширяя объектная модель автоматизации. Они определяются как часть объекта автоматизации DTE и используются для расширения объекта проекта, `ProjectItem` объекта и `Configuration` объекта. Дополнительные сведения см. в разделе [расширение объектной модели Project базы](../../extensibility/internals/extending-the-object-model-of-the-base-project.md).  
  
## <a name="multi-level-aggregation"></a>Многоуровневые статистической обработки  
 Реализацию подтип проекта, которая заключает в оболочку подтипом нижнего уровня проекта должен быть создается совместно, чтобы позволить подтип внутреннего проекта для правильной. Включает список программирования обязанности:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> Должны делегировать реализацию подтип проекта, — это заключение внутреннее подтип <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> реализация подтип внутреннего проекта для обоих <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> методы.  
  
-   <xref:EnvDTE80.IInternalExtenderProvider> Реализация подтипом проекта оболочки должны делегировать, его подтип внутреннего проекта. В частности, реализации <xref:EnvDTE80.IInternalExtenderProvider.GetExtenderNames%2A> необходимо получить строку имен из подтип внутреннего проекта, а затем выполнит объединение строк, необходимо добавить в качестве расширения.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> Необходимо создать экземпляр реализации проекта подтипа оболочки <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> объекта его внутренним подтип проекта и удерживайте ее как закрытый делегат, поскольку только для объекта конфигурации проекта базового проекта непосредственно знает, что оболочка Объект конфигурации подтип проекта существует. Подтип внешнего проекта можно изначально он хочет непосредственно обрабатывать интерфейсы для настройки и затем остальную реализацию подтип внутреннего проекта <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg.get_CfgType%2A>.  
  
## <a name="supporting-interfaces"></a>Поддержка интерфейсов  
 Базовый проект делегирует вызовы поддержка интерфейсов, добавленных с подтипом проекта, для расширения различные аспекты его реализации. Это включает в себя расширение объектов конфигурации проекта и различных свойств обозревателя объектов. Эти интерфейсы, полученного посредством обращения `QueryInterface` на `punkOuter` (указатель на `IUnknown`) агрегатора подтип внешней проекта.  
  
|Интерфейс|Подтип проекта|  
|---------------|---------------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>|Позволяет подтипом проекта для:<br /><br /> -Предоставляет реализацию <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>.<br />-Контролировать запуск отладчика, позволяя подтипом проекта предоставить собственную реализацию <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>.<br />-Отключить вычисление выражений во время разработки, их обработку `DBGLAUNCH_DesignTimeExprEval` вариантов в своей реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.QueryDebugLaunch%2A>.|  
|<xref:EnvDTE80.IInternalExtenderProvider>|Позволяет подтипом проекта для:<br /><br /> -Расширить <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> проекта для добавления или удаления независимые свойства конфигурации проекта.<br />-Расширения объекта автоматизации проекта (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>) проекта.<br /><br /> Указанные выше значения свойства берутся из <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> перечисления.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>|Позволяет подтипом проекта для сопоставления с <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> объектом по заданному объекту обзора конфигурации проекта.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBrowseObject>|Для сопоставления с подтипом проекта позволяет <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> или `VSITEMID` объект, заданный объект обзора конфигурации проекта.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>|Позволяет подтипом проекта для хранения произвольных XML-структуру данных в файл проекта (VBPROJ или VSPROJ). Эти данные не отображается в MSBuild.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>|Позволяет подтипом проекта для:<br /><br /> -Добавьте новые свойства MSBuild сохраняться.<br />-Удалите ненужные свойства из MSBuild.<br />-Запрос, текущее значение свойства MSBuild.<br />-Измените текущее значение свойства MSBuild.|  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>