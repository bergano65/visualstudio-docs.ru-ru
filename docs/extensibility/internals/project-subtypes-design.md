---
title: Проект подтипов Дизайн (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, design
ms.assetid: 405488bb-1362-40ed-b0f1-04a57fc98c56
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0b939d197bfd7e58b555ca7698f08643e3d38ef2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706447"
---
# <a name="project-subtypes-design"></a>Разработка подтипов проекта

Подтипы проекта позволяют VSPackages расширять проекты на основе Microsoft Build Engine (MSBuild). Использование агрегации позволяет повторно использовать большую часть основной [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] управляемой проектной системы, реализованной в еще не настроенном на настройку поведения для конкретного сценария.

 Ниже приведены подробные сведения об основных проектах и реализации подтипов проектов:

- Проект подтип Дизайн.

- Многоуровневая агрегация.

- Поддержка интерфейсов.

## <a name="project-subtype-design"></a>Проект подтип Дизайн

Инициализация подтипа проекта достигается путем <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> агрегирования основных объектов и <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> объектов. Эта агрегация позволяет подтипу проекта переопределить или расширить большую часть возможностей базового проекта. Подтипы проекта получают первый <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>шанс обрабатывать <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> свойства <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>с использованием, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>использование команд и управления объектами проекта с использованием. Подтипы проекта также могут расширяться:

- Объекты конфигурации проекта.

- Зависящие от конфигурации объекты.

- Независимая конфигурация просматривать объекты.

- Объекты автоматизации проекта.

- Коллекции объектов недвижимости автоматизации проекта.

Для получения дополнительной информации о расширяемости по подтипам проектов [см.](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)

### <a name="policy-files"></a>Файлы политики

Среда [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] является примером расширения базовой проектной системы с подтипом проекта при реализации файлов политики. Файл политики позволяет формировать [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] среду, управляя функциями, которые включают в себя диалоговый ящик Solution Explorer, **Добавить** диалоговую коробку Проекта, **добавить** диалоговую коробку New Item и диалоговую коробку **Свойств.** Подтип политики перекрывает и <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg>улучшает `IOleCommandTarget` <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> эти функции через и реализации.

### <a name="aggregation-mechanism"></a>Механизм агрегирования

Механизм агрегации подтипов проекта среды поддерживает несколько уровней агрегации, что позволяет внедрить расширенный подтип путем дальнейшего ароматизации ароматизированного проекта. Кроме того, поддерживающие объекты подтипа <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>проекта, такие как, предназначены для обеспечения нескольких уровней слоев. В соответствии с ограничениями правил агрегирования КОМ и КОМ подтипы проектов и базовые проекты должны быть запрограммированы на совместную программу, с тем чтобы внутренний подтип или базовый проект могли должным образом участвовать в делегировании вызовов метода и управлении подсчетами ссылок. То есть проект, который должен быть агрегирован, должен быть запрограммирован на поддержку агрегирования.

На следующей иллюстрации показано схематическое представление многоуровневой агрегации подтипов проекта.

![График Visual Studio multilevel projectflavor](../../extensibility/internals/media/vs_multilevelprojectflavor.gif)

Многоуровневая агрегация подтипов проекта состоит из трех уровней, базового проекта, который агрегируется подтипом проекта, а затем дополнительно агрегируется расширенным подтипом проекта. Цифра фокусируется на некоторых вспомогательных интерфейсах, которые [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] предоставляются как часть архитектуры подтипа проекта.

### <a name="deployment-mechanisms"></a>Механизмы развертывания

Среди многих функций базовой проектной системы, усиленной подтипом проекта, есть механизмы развертывания. Подтип проекта влияет на механизмы развертывания, реализуя <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>интерфейсы конфигураций (например, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> и), которые извлекаются при вызове queryInterface на. В сценарии, где подтип проекта и продвинутый подтип проекта добавляют `QueryInterface` различные реализации конфигурации, базовый проект требует расширенного подтипа `IUnknown`проекта. Если внутренний подтип проекта содержит реализацию конфигурации, запрашиваемой базовым проектом, то расширенный подтип проекта делегирует реализацию, предусмотренную внутренним подтипом проекта. Как механизм сохранения состояния от одного уровня агрегирования к другому, все уровни подтипов проекта реализуют <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> для сохранения несвязанных данных XML в файлах проекта. Для получения дополнительной информации смотрите [упорные данные в файле проекта MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md). <xref:EnvDTE80.IInternalExtenderProvider>реализован как механизм для извлечения расширителей автоматизации из подтипов проекта.

Следующая иллюстрация фокусируется на реализации расширителя автоматизации, в частности объекте просмотра конфигурации проекта, используемом подтипами проекта для расширения базовой проектной системы.

![График авто расширения проекта Flavor VS](../../extensibility/internals/media/vs_projectflavorautoextender.gif)

Подтипы проекта могут дополнительно расширить базовую систему проекта за счет расширения модели объектов автоматизации. Они определяются как часть объекта автоматизации DTE и используются `ProjectItem` для расширения `Configuration` объекта проекта, объекта и объекта. Для получения дополнительной [Extending the Object Model of the Base Project](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)информации см.

## <a name="multi-level-aggregation"></a>Многоуровневая агрегация

Реализация подтипа проекта, которая обертывает подтип проекта более низкого уровня, должна быть запрограммирована совместно, чтобы внутренний подтип проекта функционировал должным образом. Перечень обязанностей по программированию включает в себя:

- Реализация <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> подтипа проекта, который обертывает внутренний подтип, должна делегировать <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> реализацию <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> внутреннего подтипа проекта как для методов, так и для методов.

- Реализация <xref:EnvDTE80.IInternalExtenderProvider> подтипа проекта обертки должна делегировать его внутренний подтип проекта. В частности, <xref:EnvDTE80.IInternalExtenderProvider.GetExtenderNames%2A> реализация потребностей, чтобы получить строку имен из внутреннего подтипа проекта, а затем concatenate строки он хочет добавить в качестве расширителей.

- Реализация <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> подтипа проекта обертки должна мгновенно <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> усвоить объект его внутреннего подтипа проекта и удерживать его в качестве частного делегата, так как только объект конфигурации проекта базового проекта непосредственно знает, что объект конфигурации подтипа проекта обертки существует. Внешний подтип проекта может сначала выбрать интерфейсы конфигурации, которые он хочет обрабатывать напрямую, а затем делегировать остальное реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg.get_CfgType%2A>подтипа внутреннего проекта.

## <a name="supporting-interfaces"></a>Поддержка интерфейсов

Делегаты базового проекта призывают поддерживать интерфейсы, добавленные подтипом проекта, для расширения различных аспектов его реализации. Это включает в себя расширение объектов конфигурации проекта и различных объектов браузера свойства. Эти интерфейсы извлекаются `QueryInterface` `punkOuter` путем вызова (указателя на `IUnknown`) агрегатора подтипа внешнего проекта.

|Интерфейс|Подтип проекта|
|---------------|---------------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>|Позволяет подтипу проекта:<br /><br /> - Обеспечить <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>реализацию .<br />- Контроль запуска отладчика, позволяя подтипу проекта <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>обеспечить свою собственную реализацию .<br />- Отключить дизайн-время оценки выражения, `DBGLAUNCH_DesignTimeExprEval` надлежащим образом обработки дела в его реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.QueryDebugLaunch%2A>.|
|<xref:EnvDTE80.IInternalExtenderProvider>|Позволяет подтипу проекта:<br /><br /> - Расширить <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject> проект, чтобы добавить или удалить конфигурацию независимых свойств проекта.<br />- Расширить объект автоматизации проекта ()<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtObject>проекта.<br /><br /> Значения свойств выше взяты <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> из перечисления.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>|Позволяет подтипу проекта отображдать карту на <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> объект с учетом конфигурации проекта объекта просмотра.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBrowseObject>|Позволяет подтипу проекта отображдать карту обратно к объекту <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> или объекту, `VSITEMID` учитывая объект просмотра конфигурации проекта.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>|Позволяет подтипу проекта сохранять произвольные структурированные данные XML в файле проекта (.vbproj или .csproj). Эти данные не видны MSBuild.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>|Позволяет подтипу проекта:<br /><br /> - Добавьте новые свойства MSBuild, которые будут сохраняться.<br />- Удалите ненужные свойства из MSBuild.<br />- Запрос на текущую стоимость свойства MSBuild.<br />- Измените текущую стоимость свойства MSBuild.|

## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>
