---
title: Основные компоненты модели проекта | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project models, objects and interfaces
- project models, services
ms.assetid: b2f572d3-b26d-4846-92d1-84055fac141a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7dd3bf8f3f31b914debc6dab4eb5c4f6e7b27086
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2018
ms.locfileid: "39512227"
---
# <a name="project-model-core-components"></a>Основные компоненты модели проекта
В модели проекта разверните следующие таблицы. Таблицы предоставляют краткое описание каждого из интерфейсов и служб, указанных в модели и интерфейсы, а также службы, связанные с конкретными объектами. Кроме того в таблицах описываются другие интерфейсы, которые не являются обязательными в проект создания и обслуживания в зависимости от требований вашего проекта определенного типа.  
  
 Дополнительные сведения см. в разделе [средства просмотра символов, которые поддерживают](../../extensibility/internals/supporting-symbol-browsing-tools.md).  
  
### <a name="package-object"></a>Объект пакета  
  
|Интерфейс|Комментарии|  
|---------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|Инициализирует VSPackage в интегрированной среде разработки и делает его службы доступными в интегрированную среду разработки.|  
  
### <a name="project-factory-object"></a>Объект фабрики проекта  
  
|Интерфейс|Комментарии|  
|---------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|Управляет создания новых проектов и открытия существующих проектов.|  
  
### <a name="project-objects"></a>Объекты проекта  
  
|интерфейсов,|Комментарии|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>|Управляет Добавление и удаление элементов проекта, открывает редакторы и поддерживает сопоставление с каждой моникер документа и `VSITEMID`. Наследует от `IVsProject` и `IVsProject2`.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|Управляет свойствами навигации и отображения и предоставляет события.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>|Включает команды выполнения, аналогичны `IOleCommandTarget` для команд, таких как вырезать и переименования, которые применяются только тогда, когда фокус находится в обозревателе решений.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Служит в качестве целевой интерфейс основных команд для иерархии проекта. Это стандартный интерфейс для выполнения запросов к объектам для своей команды состояние или состояния и выполнения команд. Доступно, если не выделена в окне проекта.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Координирует сохраняемости состояния проекта. Как правило состояние проекта сохраняется как файл проекта, но может быть адаптирован к систем хранения данных, которые не основаны на файл.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|В результате проект для управления всеми аспектами сохраняемости для его элементов проекта, как файлы на диске или объекты в других системах хранения. `IVsPersistHierarchyItem2` Интерфейс используется для элементов, которые не реализуют <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> интерфейс.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Координирует взаимодействие с контролем исходного кода.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfgProvider>|Разрешает проектам управлять сведениями о конфигурации.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>|Управляет объектами конфигурации проекта, например в конфигурациях отладки или выпуска. Построение, развертывание и отладка операции выполняются через объекты конфигурации проекта.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>|Реализуется иерархий для управления удаления (разрушающее) или удалить (неразрушающее) параметры для элементов иерархии. Вызовите интерфейс запросов на `IVsHierarchyDeleteHandler` интерфейс из `IVsHierarchy` интерфейс.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsGetCfgProvider>|Предоставляет объект, который поддерживает возможность реализации `IVsCfgProvider2` COM идентификатором, отличным от объекта проекта, который реализует интерфейс `IVsHierarchy` интерфейс.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectStartupServices>|Необязательный интерфейс, реализованный в Чтобы выполнить конкретный проект расширяемый другими разработчиками. `IVsProjectStartupServices` Интерфейс позволяет зарегистрировать GUID, которое сохраняется в файл проекта, таким образом, чтобы каждый раз при загрузке проекта в файл проекта и вызовите загрузки сторонней службе идентификатор GUID VSPackage сторонних `QueryService` для этого идентификатора GUID.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelperEvents>|Реализуемый исходных иерархий в `UIHierarchy` окно, чтобы координировать операции буфера обмена, такие как вырезания, копирования и вставки. Используйте `AdviseClipboardHelperEvents` интерфейс для регистрации событий в буфер обмена.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataSource2>|Сведения о перетащенном элементе относительно его источника данных во время операции перетаскивания и вставки в окне иерархии пользовательского интерфейса. Вызывается из `IVsHierarchy` интерфейс.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataTarget>|Сведения о перетащенном элементе относительно его целевого объекта переноса во время операции перетаскивания и вставки в окне иерархии пользовательского интерфейса. Вызывается из `IVsHierarchy` интерфейс.|  
  
### <a name="configuration-object"></a>Объект конфигурации  
  
|интерфейсов,|Комментарии|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>|Сведения о конфигурации.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>|Разрешает проектам управлять сведениями о конфигурации.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|Позволяет проекту для запуска под контролем отладчика.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>|Реализуется проекты развертывания, которые выполняют операции развертывания для других проектов.|  
  
### <a name="configuration-builder-object"></a>Объект построителя конфигурации  
  
|интерфейсов,|Комментарии|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>|Управляет операцией построения конфигурации проекта.|  
  
### <a name="additional-project-objects"></a>Дополнительные объекты проекта  
  
|интерфейсов,|Комментарии|  
|----------------|--------------|  
|`IDispatch`<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>|Отображает элемент свойства в **свойства** окна.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>|Отображает выходные данные для развертывания.|  
  
 В следующей таблице представлено краткое описание каждого из служб, указанных в модели.  
  
### <a name="services"></a>Службы  
  
|Служба|Комментарии|  
|-------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|Используется VSPackages, реализации типов проекта для регистрации, что их фабрики проекта существует со средой IDE. VSPackage должен вызвать `QueryService` этой службы и зарегистрировать его фабрику проекта при `IVsPackage::SetSite` вызывается метод. Если `SetSite` метод не вызывается, проект не создается.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Предоставляет доступ к IDE внутренний, встроенные понятие текущего решения, такие как возможность перечислить проекты, создание новых проектов, легко отследить изменения в проект и т. д.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|Вызывается проектами, которые хотите принять участие в системе управления версиями.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|Поддерживает таблицу открытых документов, чтобы определить, является ли один или несколько элементов проекта уже открыты.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|Содержит интерфейсы и методы, вызываемые фактически открыть элемент проекта, с помощью стандартного редактора или определенном редакторе.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|Требуется вызывать все проекты при их добавить, удалить или переименовать их элементов.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|Управляет изменений к файлу или каталогу и уведомляет клиентов, когда выбранные файлы были изменены на диске.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|Должен вызываться для всех проектов и редакторов до их измененные элементы или сохранить их.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|Управляет порядком операций сборки и развертывания для конфигурации проекта.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|Предоставляет доступ к службам низкоуровневый отладчик, используемый для большинства элементов управления для отладки.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|Включает пакеты VSPackage доступ к сведениям о выбранных и обеспечивает взаимодействие с **свойства** окна.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Предоставляет основные функциональные возможности интегрированной среды разработки, связанные с пользовательского интерфейса, такие как возможность для создания и перечислить окон инструментов и окон документов или сообщить об ошибке для пользователя.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|Предоставляет доступ к строке состояния интегрированной среды разработки.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibility3>|Используется для реализации модели автоматизации. В модели проекта, будет возвращать объект свойств, которая позволяет создает экземпляр этого объекта.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|Используется для реализации событий в буфер обмена на объект проекта в иерархии. `SVsUIHierWinClipboardHelper` позволяет правильно дескриптор вырезания, копирования и вставки.|  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Контрольный список: Создание типов проектов](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Не в сборке: использование HierUtil7 проект классов для реализации типа проекта (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [Вспомогательные средства просмотра символов](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [Элементы модели проекта](../../extensibility/internals/elements-of-a-project-model.md)