---
title: "Основные компоненты модели проекта | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "проект модели, объекты и интерфейсы"
  - "проект модели, службы"
ms.assetid: b2f572d3-b26d-4846-92d1-84055fac141a
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# Основные компоненты модели проекта
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Следующие таблицы развернут на модели проекта.  Описания таблиц, присутствующие краткое интерфейсов и служб, определенных в модели, и интерфейсы и службами, связанными с конкретными объектами.  Кроме того, таблицы углубленную детализацию другие интерфейсы, которые являются необязательными при создании и обслуживании " проекта в зависимости от требований конкретного определенного типа проекта.  
  
 Дополнительные сведения см. в разделе [Вспомогательные средства просмотра символов](../../extensibility/internals/supporting-symbol-browsing-tools.md).  
  
### Объект пакета  
  
|Интерфейс|Комментарии|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|Инициализирует VSPackage в интегрированной среде разработки службы и делает его доступным для интегрированной среде разработки.|  
  
### Объект фабрики проектов  
  
|Интерфейс|Комментарии|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|Создать новые проекты управления и открытия существующих проектов.|  
  
### Объекты проекта  
  
|Интерфейсы|Комментарии|  
|----------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>|Управляет добавление и удаление элементов проекта, редакторов открытых и поддерживает сопоставление между каждым моникером документа и `VSITEMID`.  Наследует `IVsProject` и  `IVsProject2`.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|Свойства навигации и отображения элементов управления и предоставляют события.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>|Включает выполнение команды, подобный этому из `IOleCommandTarget` для команд как вырезание и переименование, которые применяются только в том случае, если фокус в обозревателе решений.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Служит в качестве основной интерфейс целевого объекта команды для иерархии проекта.  Стандартный интерфейс для запросов объекты, их состояния команды или состояния и выполнения команд.  Доступен, когда фокус не будет переведен в окне проекта.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Координирует сохранение состояния проекта.  Как правило, состояние проекта сохраняется как файл проекта, но может быть приспособлено к системам хранения, которые не на основе файлов.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|Содержит проекты управлять всеми аспектами сохраняемости для его элементов проекта или как дисковые файлы или объекты в других системах хранения.  `IVsPeristHierarchyItem2` интерфейс используется для элементов, которые не реализуют  <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> интерфейс.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Координирует взаимодействие с элементом управления исходным кодом.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfgProvider>|Включает проекты управлять сведения о конфигурации.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>|Управляет объектами конфигурации проекта, например конфигурации отладки и выпуска.  Построение, развертывание и отладка операции скоординировано через объекты конфигурации проекта.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>|Реализуется иерархиями для наблюдения за удаление \(разрушительную\) или удаление параметров \(без удаления\) для элементов иерархии.  Интерфейс запроса для вызова `IVsHierarchyDeleteHandler` интерфейс из  `IVsHierarchy` интерфейс.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsGetCfgProvider>|Предоставляет параметр реализации иметь объект, поддерживающий `IVsCfgProvider2` интерфейс на другой идентификатор модели COM, чем объект проекта, реализующий  `IVsHierarchy` интерфейс.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectStartupServices>|Необязательный интерфейс, реализованный для этого проекта раздвижным другими разработчиками.  `IVsProjectStartupServices` интерфейс позволяет сторонним VSPackage для регистрации идентификатора GUID, что упорствуете в файл проекта, поэтому каждый раз, когда проект загрузит, загрузке сторонние GUID службы в файл проекта и вызов  `QueryService` для этого идентификатора GUID.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelperEvents>|Реализуется иерархиями источника в выражении `UIHierarchy` окно, чтобы координировать операции буфера обмена в качестве вырезать, копировать и вставить.  Используйте `AdviseClipboardHelperEvents` интерфейс для регистрации событий буфера обмена.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataSource2>|Предоставляет сведения о перетащенном элемента относительно его источнику данных во время операции перетаскивания в окне иерархии пользовательского интерфейса.  Вызывается из `IVsHierarchy` интерфейс.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataTarget>|Предоставляет сведения о перетащенном элемента относительно его целевому объекту вставки во время операции перетаскивания в окне иерархии пользовательского интерфейса.  Вызывается из `IVsHierarchy` интерфейс.|  
  
### Объект конфигурации.  
  
|Интерфейсы|Комментарии|  
|----------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>|Предоставляет сведения о конфигурации.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>|Включает проекты управлять сведения о конфигурации.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|Содержит проекты выполняться под контролем отладчика.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>|Реализуется проектами развертывания, которые выполняют операции развертывания для других проектов.|  
  
### Объект построителя конфигурации  
  
|Интерфейсы|Комментарии|  
|----------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>|Управляет операция построения конфигурации проекта.|  
  
### Дополнительные объекты проекта  
  
|Интерфейсы|Комментарии|  
|----------------|-----------------|  
|`IDispatch`<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>|Указывает свойства элементов в **Свойства** окна.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>|Отображает вывод для развертывания.|  
  
 В следующей таблице представлены краткие описания служб, определенных в модели проекта.  
  
### Службы  
  
|Служба|Комментарии|  
|------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|Используется VSPackages типы проектов того, регистрируемый реализовать их фабрики проектов с интегрированной средой разработки.  В VSPackage должно вызвать `QueryService` для этой службы и зарегистрируйте его фабрики проектов, когда  `IVsPackage::SetSite` вызывается метод.  Если `SetSite` не вызывается метод создан проект.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Предоставляет доступ к интегрированной среды разработки внутренним, встроенную понятие текущего решения, например возможность перечисления проектов создает новые проекты, принимающий уведомление об изменениях проекта и т д|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|Вызывается проектами, которые желают участвовать в системе управления версиями.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|Поддерживает таблицу открытых документов, чтобы определить, открываются, является ли один или несколько элементов проекта уже.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|Содержит интерфейсы и методы, вызываемые фактически, чтобы открыть элемент проекта с помощью стандартного редактор или конкретным редактором.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|Необходим вызванных всеми проектами, когда они добавляют, удалите или переименуйте их элементы.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|Управления изменяются к файлу или каталогу и уведомляющие клиенты, если выбранные файлы были изменены на диске.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|Необходим вызванных всеми проектами и редакторами до необходимости измененные элементы или сохранить их.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|Управляет порядок операций построения и развертывания для конфигураций проекта.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|Предоставляет доступ к службам низкоуровневым отладчика, используемым для большинства элементов управления отладки.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|Включает доступ к сведениям о текущем выделениях VSPackages, и включает сообщение с **Свойства** окна.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Предоставляет основные функциональные возможности пользовательского интерфейс\-родственную интегрированной среды разработки, например возможность создания и отображения окна инструментов или окна документа или сообщить пользователю ошибка.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|Предоставляет доступ к строке состояния интегрированной среды разработки.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibility3>|Используется для реализации модели автоматизации.  В модель проекта, необходимо возвратить объект свойств, позволяющий создать экземпляр этого объекта.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|Используется для реализации события буфера обмена в объекте проекта в иерархии.  `SVsUIHierWinClipboardHelper` позволяет правильно обработать вырезать, копировать и вставлять операции.|  
  
## См. также  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Контрольный список: Создание новых типов проектов](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Not in Build: Using HierUtil7 Project Classes to Implement a Project Type \(C\+\+\)](http://msdn.microsoft.com/ru-ru/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [Вспомогательные средства просмотра символов](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [Элементы модели проекта](../../extensibility/internals/elements-of-a-project-model.md)