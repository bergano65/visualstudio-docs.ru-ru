---
title: Проект подтипы разработки | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, design
ms.assetid: 405488bb-1362-40ed-b0f1-04a57fc98c56
caps.latest.revision: 33
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0e7cd96324e5a2bbd6c9b0acf4125bc0450cfd06
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62430553"
---
# <a name="project-subtypes-design"></a>Разработка подтипов проекта
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Подтипов проекта позволяют пакеты VSPackage расширяют проектов на основании Microsoft Build Engine (MSBuild). Использование статистической обработки позволяет повторно использовать основную часть реализации в системе проектов core управляемых [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , но по-прежнему настройки поведения для конкретного сценария.  
  
 Следующие разделы подробно описаны основные проектирование и реализацию подтипов проекта.  
  
- Структура подтип проекта.  
  
- Многоуровневые статистической обработки.  
  
- Поддержка интерфейсов.  
  
## <a name="project-subtype-design"></a>Проектирование подтип проекта  
 Инициализация подтипом проекта достигается за счет объединения основной <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> объектов. Объединение позволяет подтипа проекта для переопределения или изменения большинство возможностей базового проекта. Подтипов проекта получить первый шанс обработки свойств с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>, команд с использованием <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>и проект элемента управления с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>. Также можно расширить подтипов проекта:  
  
- Объекты конфигурации проекта.  
  
- Объекты, зависящие от конфигурации.  
  
- Обзор конфигурациями объектов.  
  
- Объекты автоматизации проекта.  
  
- Автоматизация свойства коллекций проектов.  
  
  Дополнительные сведения о расширяемости для подтипов проекта, см. в разделе [свойства и методы, расширенные подтипами проектов](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md).  
  
##### <a name="policy-files"></a>Файлы политики  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Среда предоставляет пример расширения базовой системы проектов с подтипом проекта, в своей реализации файлы политики. Файл политики позволяет формирование [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] среды, управляя функциональные возможности, включая обозреватель решений **добавить проект** диалоговом окне **Добавление нового элемента** диалоговое окно и  **Свойства** диалоговое окно. Подтип политики переопределяет и расширяет эти функции через <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg>, `IOleCommandTarget` и <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> реализаций.  
  
##### <a name="aggregation-mechanism"></a>Механизм статистической обработки  
 Механизм статистической обработки подтип проекта среды поддерживает несколько уровней статистической обработки, что позволяет дополнительно подтип, для реализации дополнительных flavoring предпочтительный проект. Кроме того, подтипа проекта вспомогательные объекты, такие как <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>, позволяют использовать несколько уровней архитектуры. В соответствии с ограничениями COM и COM правила агрегирования, подтипов проекта и проекта базовых проектов должны быть запрограммированы совместно, чтобы внутренний подтип или базового проекта могли надлежащим образом участвовали в делегировании вызовов методов и управление счетчиков ссылок . То есть проекте, которые должны быть статистически вычислена должен быть запрограммированы для поддержки статистической обработки.  
  
 Ниже показан схематически статистического вычисления подтип многоуровневого проекта.  
  
 ![График многоуровневой projectflavor Visual Studio](../../extensibility/internals/media/vs-multilevelprojectflavor.gif "VS_MultilevelProjectFlavor")  
Подтип многоуровневого проекта  
  
 Является агрегатом подтип многоуровневого проекта состоит из трех уровней, в базовый проект, который является статистическая обработка проводится путем подтипом проекта, а затем Дополнительно статистическая обработка проводится путем подтипа проекта расширенной. Рис посвящена некоторым вспомогательных интерфейсов, которые предоставляются как часть [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] архитектура подтип проекта.  
  
##### <a name="deployment-mechanisms"></a>Механизмы развертывания  
 Среди многих базовой системы проектов функциональные возможности, дополнены подтипом проекта — это механизмы развертывания. Подтип проекта влияет механизмы развертывания путем реализации интерфейсов конфигурации (таких как <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>), извлекаются путем вызова QueryInterface для <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>. В сценарии, где подтипа проекта и подтипа проекта расширенной добавьте реализации другой конфигурации, вызывает базового проекта `QueryInterface` на подтипа проекта расширенной `IUnknown`. Если внутренний подтип проекта содержит реализацию конфигурации, которая запрашивает базового проекта, подтипа проекта расширенной делегирует реализацию, предоставляемую внутреннего подтипа проекта. Как механизм сохранения состояния уровень статистической обработки одной реализации всех уровней подтипов проекта <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> для сохранения не сборки связанные XML-данных в файлы проекта. Дополнительные сведения см. в разделе [сохранение данных в файле проекта MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md). <xref:EnvDTE80.IInternalExtenderProvider> реализуется как механизм для извлечения расширителей автоматизации из подтипов проекта.  
  
 Ниже рассматривается реализация расширителей автоматизации, объект обзора конфигурации проекта в частности, подтипов проекта, используемый для расширения системы базового проекта.  
  
 ![График авто расширения проекта Flavor VS](../../extensibility/internals/media/vs-projectflavorautoextender.gif "VS_ProjectFlavorAutoExtender")  
Расширения автоматизации подтип проекта.  
  
 Подтипов проекта можно расширить базовой системы проектов, расширив объектной модели автоматизации. Они определяются как часть объект автоматизации DTE и используются для расширения объекта проекта, `ProjectItem` объекта и `Configuration` объекта. Дополнительные сведения см. [расширение модели объекта базового проекта](../../extensibility/internals/extending-the-object-model-of-the-base-project.md).  
  
## <a name="multi-level-aggregation"></a>Многоуровневые статистической обработки  
 Реализация подтип проекта, который заключает в оболочку подтипом нижнего уровня проекта должен быть создается совместно, чтобы позволить внутреннего подтипа проекта для правильной. Включает список программирования обязанности:  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> Должны делегировать реализацию подтипа проекта, который является оболочкой внутренний подтип <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> реализацию внутреннего подтипа проекта для обоих <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> методы.  
  
- <xref:EnvDTE80.IInternalExtenderProvider> Реализации оболочки подтипа проекта следует делегировать, его внутренний подтип проекта. В частности, реализации <xref:EnvDTE80.IInternalExtenderProvider.GetExtenderNames%2A> необходимо получить строку имен из внутреннего подтипа проекта, а затем выполнит объединение строк, необходимо добавить в качестве расширения.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> Реализации оболочки подтипа проекта необходимо создать экземпляр <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> объекта его внутренний подтип проекта и удерживайте его как закрытый делегат, так как только объект конфигурации проекта базового проекта непосредственно знает, что оболочка существует объект конфигурации подтипа проекта. Внешним подтипом проекта можно сначала выберите интерфейсов конфигурации, оно может обработать напрямую, а затем делегирует rest для реализации внутреннего подтипа проекта <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg.get_CfgType%2A>.  
  
## <a name="supporting-interfaces"></a>Поддержка интерфейсов  
 Базовый проект делегирует вызовы поддержка интерфейсов, добавленные подтипом проекта, чтобы расширить различные аспекты его реализации. Это включает в себя расширение объектов конфигурации проекта и различных свойств обозревателя объектов. Эти интерфейсы извлекаются путем вызова `QueryInterface` на `punkOuter` (указатель на `IUnknown`) агрегатора подтип внешний проект.  
  
|Интерфейс|Подтип проекта|  
|---------------|---------------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>|Разрешает подтипу проекта:<br /><br /> -Предоставлять реализацию метода <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>.<br />-Контролировать запуск отладчика, позволяя подтипом проекта, чтобы предоставить собственную реализацию <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>.<br />-Отключить вычисление выражений во время разработки с соответствующей обработкой `DBGLAUNCH_DesignTimeExprEval` вариантов в своей реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.QueryDebugLaunch%2A>.|  
|<xref:EnvDTE80.IInternalExtenderProvider>|Разрешает подтипу проекта:<br /><br /> -Расширить <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> проекта для добавления или удаления независимых свойства конфигурации проекта.<br />-Расширения автоматизации объекта проекта (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>) проекта.<br /><br /> Значения свойств выше берутся из <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> перечисления.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>|Разрешает подтипу проекта для отображения обратно в <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> объект передан объект обзора конфигурации проекта.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBrowseObject>|Разрешает подтипу проекта для отображения обратно в <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> или `VSITEMID` объект, которому передан объект обзора конфигурации проекта.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>|Разрешает подтипу проекта для хранения произвольных XML-структуру данных в файл проекта (VBPROJ или csproj). Эти данные не отображается в MSBuild.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>|Разрешает подтипу проекта:<br /><br /> — Добавление новых свойств MSBuild, должна быть сохранена.<br />-Удалите ненужные свойства из MSBuild.<br />-Запрос для текущего значения свойства MSBuild.<br />— Изменение текущего значения свойства MSBuild.|  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>
