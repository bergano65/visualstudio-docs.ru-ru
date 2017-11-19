---
title: "Основные компоненты модели проекта | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project models, objects and interfaces
- project models, services
ms.assetid: b2f572d3-b26d-4846-92d1-84055fac141a
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c7759a2394f2cda19f875a85a22c4a674fee8964
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="project-model-core-components"></a>Основные компоненты модели проекта
В модели проекта разверните следующие таблицы. Таблицы представлены краткие описания интерфейсов и служб, описанных в модели и интерфейсы и службы, связанные с конкретными объектами. Кроме того в таблице приведено описание других интерфейсов, которые не являются обязательными в проект создания и обслуживания, в зависимости от требований вашего проекта определенного типа.  
  
 Дополнительные сведения см. в разделе [средства обзора поддержка символов](../../extensibility/internals/supporting-symbol-browsing-tools.md).  
  
### <a name="package-object"></a>Объект пакета  
  
|Интерфейс|Комментарии|  
|---------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|Инициализирует VSPackage Интегрированной среды разработки и делает доступными ее служб в интегрированную среду разработки.|  
  
### <a name="project-factory-object"></a>Объект фабрики проектов  
  
|Интерфейс|Комментарии|  
|---------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|Управляет создание новых проектов и открытия существующих проектов.|  
  
### <a name="project-objects"></a>Объекты проекта  
  
|Интерфейсы|Комментарии|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>|Управляет Добавление и удаление элементов проекта, открывается редакторы и поддерживает сопоставление с каждой моникер документа и `VSITEMID`. Наследует от `IVsProject` и `IVsProject2`.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|Управляет свойствами навигации и отображения и предоставляет события.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>|Включает команду выполнения аналогичен `IOleCommandTarget` для команд, например вырезания и переименования, применяемые только тогда, когда фокус находится в обозревателе решений.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Служит в качестве интерфейса целевого основных команд для иерархии проекта. Это стандартный интерфейс для выполнения запросов к объектам для их команды состояние или состояние и выполнения команд. Доступно, если не выделена в окне проекта.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Координаты сохраняемости состояния проекта. Как правило состояния проекта сохраняется как файл проекта, но можно адаптировать для систем хранения данных, которые не основаны на файл.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|В результате проект для управления всеми аспектами сохраняемости для его элементов проекта, либо как файлы на диске или объекты в других систем хранения данных. `IVsPeristHierarchyItem2` Интерфейс используется для элементов, которые не реализуют <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> интерфейса.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Координирует взаимодействие с контролем исходного кода.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfgProvider>|Позволяет управлять сведениями о конфигурации проекты.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>|Управляет объектами конфигурации проекта, например конфигураций отладки и выпуска. Построение, развертывание и отладка операций координируются через объекты конфигурации проекта.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>|Реализован иерархий, чтобы управлять удаления (разрушающее) или удалить (неразрушающее) параметры для элементов иерархии. Вызывает запрос на `IVsHierarchyDeleteHandler` интерфейс из `IVsHierarchy` интерфейса.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsGetCfgProvider>|Предоставляет объект, который поддерживает возможность реализации `IVsCfgProvider2` другое удостоверение COM, чем проект объект, реализующий интерфейс `IVsHierarchy` интерфейс.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectStartupServices>|Необязательный интерфейс, реализованный осуществлять расширяемой проекта другими разработчиками. `IVsProjectStartupServices` Интерфейс позволяет VSPackage сторонних зарегистрировать GUID, который сохраняется в файле проекта, чтобы каждый раз при загрузке проекта загружать GUID сторонние службы в файл проекта и вызовите `QueryService` для этого идентификатора GUID.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelperEvents>|Реализуемый исходных иерархий в `UIHierarchy` окна, чтобы координировать операции буфера обмена, например вырезания, копирования и вставки. Используйте `AdviseClipboardHelperEvents` интерфейс для регистрации событий в буфер обмена.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataSource2>|Сведения о сбросе перетаскиваемого элемента относительно его источника данных во время операции перетаскивания и вставки в окне иерархии пользовательского интерфейса. Вызывается из `IVsHierarchy` интерфейса.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataTarget>|Сведения о сбросе перетаскиваемого элемента относительно его конечного расположения сброса во время операции перетаскивания и вставки в окне иерархии пользовательского интерфейса. Вызывается из `IVsHierarchy` интерфейса.|  
  
### <a name="configuration-object"></a>Объект конфигурации  
  
|Интерфейсы|Комментарии|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>|Сведения о конфигурации.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>|Позволяет управлять сведениями о конфигурации проекты.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|В результате проект для работы под управлением отладчика.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>|Реализован проекты развертывания, которые выполняют операции развертывания для других проектов.|  
  
### <a name="configuration-builder-object"></a>Объект конфигурации построителя  
  
|Интерфейсы|Комментарии|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>|Управляет операцией построения конфигурации проекта.|  
  
### <a name="additional-project-objects"></a>Дополнительные объекты проекта  
  
|Интерфейсы|Комментарии|  
|----------------|--------------|  
|`IDispatch`<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>|Отображает элемент свойства в **свойства** окна.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>|Отображает выходные данные для развертывания.|  
  
 В следующей таблице приведено краткое описание каждого из служб, описанных в модели проекта.  
  
### <a name="services"></a>Службы  
  
|Служба|Комментарии|  
|-------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|Использовать пакеты VSPackage, реализовывать типы проектов, чтобы зарегистрировать их фабрики проектов имела интегрированной среды разработки. Необходимо вызвать VSPackage `QueryService` для этой службы и зарегистрируйте его фабрики проектов при `IVsPackage::SetSite` вызывается метод. Если `SetSite` метод не вызван, проект не создается.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Предоставляет доступ к интегрированной среде разработки внутренний, встроенные понятие текущего решения, такие как возможность перечислить проекты, создавать новые проекты, легко отследить изменения в проект и т. д.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|Вызывается средой проекты, которые хотите принять участие в системе управления версиями.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|Поддерживает таблицу, открытых документов, чтобы определить, является ли один или несколько элементов проекта уже открыт.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|Содержит интерфейсы и методы, вызываемые фактически открыть элемент проекта с помощью стандартного редактора или специальный редактор.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|Должен вызываться всеми проектами при их добавить, удалить или переименовать их элементы.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|Управляет изменения в файл или каталог и сообщает клиенту, когда выбранные файлы были изменены на диске.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|Должен вызываться по всем проектам и редакторы до их измененные элементы или сохранить их.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|Управляет порядком операций построения и развертывания для конфигурации проекта.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|Предоставляет доступ к службам отладчика низкого уровня, используемый для большинства элементов управления для отладки.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|Позволяет пакетам VSPackage доступ к сведениям о текущий выбор, а связь с **свойства** окна.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Предоставляет базовые функциональные возможности интегрированной среды разработки, связанные с Пользовательским интерфейсом, такие как возможность создания и перечислить окна инструментов или окна документа или сообщение об ошибке для пользователя.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|Предоставляет доступ к строке состояния интегрированной среды разработки.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibility3>|Используется для реализации модели автоматизации. В модели проекта, будет возвращать объект свойств, которая позволяет создает экземпляр этого объекта.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|Используется для реализации событий, буфер обмена для объекта в иерархии проекта. `SVsUIHierWinClipboardHelper`обеспечивает правильное дескриптор вырезания, копирования и вставки.|  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Контрольный список: Создание новых типов проектов](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Не в сборке: использование HierUtil7 проекта классов для реализации тип проекта (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [Вспомогательные средства обзора символ](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [Элементы модели проекта](../../extensibility/internals/elements-of-a-project-model.md)