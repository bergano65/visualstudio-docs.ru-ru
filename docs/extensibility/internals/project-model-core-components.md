---
title: Основные компоненты модели проекта (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project models, objects and interfaces
- project models, services
ms.assetid: b2f572d3-b26d-4846-92d1-84055fac141a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 34f65973f0f3edc1dd6264c32d165503dca78681
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706542"
---
# <a name="project-model-core-components"></a>Основные компоненты модели проекта
Следующие таблицы расширяются на модели проекта. В таблицах представлены краткие описания интерфейсов и служб, определенных в модели, а также интерфейсов и служб, связанных с конкретными объектами. Кроме того, в таблицах подробно описаны другие интерфейсы, которые являются необязательными при создании и обслуживании проекта в зависимости от требований конкретного типа проекта.

 Для получения дополнительной [информации](../../extensibility/internals/supporting-symbol-browsing-tools.md)см.

### <a name="package-object"></a>Объект упаковки

|Интерфейс|Комментарии|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|Инициализирует VSPackage в IDE и делает его услуги доступными для IDE.|

### <a name="project-factory-object"></a>Объект «Фабрика проекта»

|Интерфейс|Комментарии|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|Управляет созданием новых проектов и открытием существующих проектов.|

### <a name="project-objects"></a>Объекты проекта

|Интерфейсы|Комментарии|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>|Управляет добавлением и удалением элементов проекта, открывает редакторы и поддерживает отображение между каждым псевдонимом документа и `VSITEMID`. Наследует `IVsProject` от `IVsProject2`и .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|Управляет навигационными и отображаемыми свойствами и предоставляет события.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>|Включает выполнение команд, `IOleCommandTarget` аналогичное выполнению команд, таких как Cut и Rename, которые применяются только при фокусе в Solution Explorer.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Служит в качестве основного интерфейса цели команды для иерархии проектов. Это стандартный интерфейс для запроса объектов для их состояния команды или состояния и выполнения команд. Доступно, когда вы не сосредоточены в окне проекта.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Координирует сохранение состояния проекта. Как правило, состояние проекта хранится в виде файла проекта, но может быть адаптировано к системам хранения данных, которые не основаны на файлах.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|Позволяет проекту управлять всеми аспектами сохранения элементов проекта, как файлы на диске, либо объекты в других системах хранения. Интерфейс `IVsPersistHierarchyItem2` используется для элементов, которые <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> не реализуют интерфейс.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Координирует взаимодействие с управлением исходным кодом.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfgProvider>|Позволяет проектам управлять информацией о конфигурации.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>|Управляет объектами конфигурации проекта, такими как конфигурации Debug/Release. Операции сборки, развертывания и отладки координируются через объекты конфигурации проекта.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>|Реализовано иерархиями для управления удаленными (разрушительными) или удаленными (неразрушающими) вариантами элементов иерархии. Вызов интерфейса запроса `IVsHierarchyDeleteHandler` на `IVsHierarchy` интерфейсе из интерфейса.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsGetCfgProvider>|Предоставляет возможность реализации объекта, поддерживающего `IVsCfgProvider2` интерфейс на другой идентификации COM, `IVsHierarchy` чем объект проекта, который реализует интерфейс.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectStartupServices>|Дополнительный интерфейс реализован, чтобы сделать ваш проект расширяемым другими разработчиками. Интерфейс `IVsProjectStartupServices` позволяет стороннему VSPackage зарегистрировать GUID, который вы сохраняете в файле проекта, так что каждый раз, когда ваш `QueryService` проект загружается, вы загружаете стороннюю службу GUID в файл проекта и призываете к этому GUID.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelperEvents>|Реализовано иерархиями источников в `UIHierarchy` окне для координации операций буфера обмена, таких как вырезать, копировать и вставить. Используйте `AdviseClipboardHelperEvents` интерфейс для регистрации событий буфера обмена.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataSource2>|Предоставляет информацию о перетасанном элементе относительно источника данных во время операции перетаскивания и падения в окне иерархии uI. Вызывается `IVsHierarchy` из интерфейса.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataTarget>|Предоставляет информацию о перетасанном элементе относительно цели падения во время операции перетаскивания и падения в окне иерархии uI. Вызывается `IVsHierarchy` из интерфейса.|

### <a name="configuration-object"></a>Объект конфигурации

|Интерфейсы|Комментарии|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>|Предоставляет информацию о конфигурации.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>|Позволяет проектам управлять информацией о конфигурации.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|Позволяет выполнять проект под контролем отладчика.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>|Реализованы проектами развертывания, выполняющие операции развертывания для других проектов.|

### <a name="configuration-builder-object"></a>Объект настройки builder

|Интерфейсы|Комментарии|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>|Управляет операцией построения конфигурации проекта.|

### <a name="additional-project-objects"></a>Дополнительные объекты проекта

|Интерфейсы|Комментарии|
|----------------|--------------|
|`IDispatch`<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>|Отображает свойства элементов в окне **Свойств.**|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>|Отображает выводы для развертывания.|

 В следующей таблице представлены краткие описания услуг, определенных в модели проекта.

### <a name="services"></a>Службы

|Служба|Комментарии|
|-------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|Используется VSPackages, которые реализуют типы проектов, чтобы зарегистрировать, что их проектная фабрика существует с IDE. Ваш VSPackage `QueryService` должен позвонить на эту `IVsPackage::SetSite` услугу и зарегистрировать свою фабрику проекта, когда метод называется. Если `SetSite` метод не вызывается, ваш проект не вызывается мгновенно.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Обеспечивает доступ к внутреннему, встроенному понятию IDE текущего решения, например, к возможности перечислять проекты, создавать новые проекты, обращать внимание на изменения проектов и так далее.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|Вызывается по проектам, которые хотят участвовать в управлении исходным источником.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|Поддерживает таблицу открытых документов, чтобы определить, открыт ли один или несколько элементов проекта.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|Содержит интерфейсы и методы, призванные фактически открыть элемент проекта с помощью стандартного редактора или конкретного редактора.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|Требуется вызываться всеми проектами при добавлении, удалении или переименовании их элементов.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|Управляет изменениями в файле или каталоге и уведомляет клиентов, когда выбранные файлы были изменены на диске.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|Требуется, чтобы быть вызваны всеми проектами и редакторами, прежде чем они грязные элементы или сохранить их.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|Управляет порядком операций сборки и развертывания для конфигураций проектов.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|Обеспечивает доступ к низкоуровневым службам отладчика, используемым для большинства элементов управления отладки.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|Предоставляет VSPackages доступ к информации о текущих выборах и обеспечивает связь с окном **Properties.**|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Предоставляет основные функции IDE, связанные с пользовательским интерфейсом, такие как возможность создавать и перечислять окна инструментов или окна документирования или сообщать пользователю об ошибке.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|Обеспечивает доступ к панели статуса IDE.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibility3>|Используется для реализации модели автоматизации. В модели проекта вы вернете объект свойств, который позволяет создать экземпляр этого объекта.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|Используется для реализации событий буфера обмена на объекте проекта в иерархии. `SVsUIHierWinClipboardHelper`позволяет правильно обрабатывать операции разреза, копирования и вставки.|

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Контрольный список. Создание типов проектов](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Не в сборке: использование классов проектов HierUtil7 для реализации типа проекта](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)
- [Вспомогательные средства просмотра символов](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Элементы модели проекта](../../extensibility/internals/elements-of-a-project-model.md)
