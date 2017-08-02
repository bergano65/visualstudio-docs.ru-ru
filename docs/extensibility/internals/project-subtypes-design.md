---
title: "Подтипы разработки проекта | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "подтипы проекта, разработки"
ms.assetid: 405488bb-1362-40ed-b0f1-04a57fc98c56
caps.latest.revision: 32
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 32
---
# Подтипы разработки проекта
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Подтипы проекта позволяют расширять проекты VSPackages, основанные на системе построения Майкрософт \(msbuild\).  Использование агрегата позволяет повторно использовать большую часть системы проекта, реализованной в управляемой core [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] но по\-прежнему настраивать функциональности для конкретного сценария.  
  
 В следующих подразделах проектирования и углубленную детализацию базовую реализацию подтипов проекта:  
  
-   Конструктор подтипа проекта.  
  
-   Многоуровневый агрегат.  
  
-   Поддержка интерфейсов.  
  
## Конструктор подтипа проекта  
 Инициализация подтипа проекта достигается путем статистического вычисления main <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> и  <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> объекты.  Это статистическое выражение позволяет подтип проекта для переопределения или расширить большинство возможностей базового проекта.  Подтипы проекта получают возможность настроить свойства с помощью первый <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>с помощью команды  <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> и  <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>и управление с помощью элемента проекта  <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>.  Подтипы проекта также могут расширять:  
  
-   Объекты конфигурации проекта.  
  
-   Объекты Конфигурация\-зависимой ячейки.  
  
-   Конфигурация\-независимо просмотр объектов.  
  
-   Объекты автоматизации проектов.  
  
-   Коллекции свойств автоматизации проектов.  
  
 Дополнительные сведения о расширяемости для подтипов проекта см. в разделе [Свойства и методы дополнено подтипы проектов](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md).  
  
##### Файлы политики  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] среда пример расширения базовую систему проекта с подтипом проекта в своей реализации файлов политики.  Файл политики позволяет являющаяся [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] среда для управления функции, включающие обозревателе решений  **Добавьте в проект** откроется диалоговое окно  **Добавление нового элемента** диалоговое окно и  **Свойства** диалоговое окно.  Подтип политики переопределяет эти функции и увеличивается до конца <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg>"  `IOleCommandTarget` и  <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> реализации.  
  
##### Механизм статистической обработки  
 Механизм статистической обработки подтипа проекта среды поддерживает несколько уровней статистической обработки, таким образом разрешая расширенный подтип, который реализует более дальнеиший flavoring приправленный проект.  Кроме того, вспомогательные объекты, такие как подтипа проекта <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>выберите проектирование, чтобы разрешить использовать несколько уровней наслаивать.  0Nв Соответствии с ограничениями правилами статистической обработки модели COM и модели COM, подтипы проекта и базовые проекты должны быть запрограммированным совместно, чтобы включить внутренний или подтип базовый проект правильно участвовать в делегируя вызовах метода и счетчики ссылок управления.  Иными словами, проект будет статистической обработке должен быть запрограммирован для поддержки статистической обработки.  
  
 На следующем рисунке показано схематическое представление многоуровневого агрегата подтипа проекта.  
  
 ![График Visual Studio multilevel projectflavor](~/docs/extensibility/internals/media/vs_multilevelprojectflavor.gif "VS\_MultilevelProjectFlavor")  
Многоуровневый подтип проекта  
  
 Многоуровневый агрегат подтипа проекта состоит из 3 уровней базового проекта, статистическая обработка подтипом проекта, затем далее статистическая обработка проводится дополнительным подтипом данного проекта.  Диаграмма фокусируется на некоторых поддержка интерфейсов, предоставляемых как часть [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] архитектура подтипа проекта.  
  
##### Механизмы развертывания  
 Улучшенные функциональные возможности для множества из базового системы проектов подтипом проекта механизмы развертывания.  Подтип проекта влияет на механизмы развертывания, реализовав интерфейсы конфигурации \(например, <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> и  <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>\), восстанавливается путем вызова QueryInterface on  <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>.  В сценарии, где и подтип проекта, и предварительного подтип проекта добавить различные реализации конфигурации основные вызовы проекта `QueryInterface` в расширенном подвиде проекта  `IUnknown`.  Если внутренний подтип проекта содержит реализацию конфигурации, базовый проект запрашивает, необходимые делегаты подтипа проекта в реализации заданных внутренним подтипом данного проекта.  По мере того, как механизм для сохранения состояния из одного слоя в другой статистической обработки всех уровней " подтипов проекта <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> сохранение non\-построение связанных данных XML в файлы проекта.  Дополнительные сведения см. в разделе [Сохранение данных в файле проекта MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md).  <xref:EnvDTE80.IInternalExtenderProvider> реализует как механизм для получения расширители автоматизации из подтипов проекта.  
  
 Ниже рассматриваются реализации расширителей автоматизации, конфигурация проекта обзор объект в частности, используемое для подтипов проекта, чтобы расширить основную систему проектов.  
  
 ![График авто расширения проекта Flavor VS](~/docs/extensibility/internals/media/vs_projectflavorautoextender.gif "VS\_ProjectFlavorAutoExtender")  
Расширитель автоматизации подтипа проекта.  
  
 Подтипы проектов могут дальше расширить систему проекта, расширяющие базовую объектную модель автоматизации.  Они указываются как часть объекта автоматизации DTE и используются для расширения проекта, объект `ProjectItem` объект и  `Configuration` объект.  Дополнительные сведения см. в разделе [Расширение модели объекта базового проекта](../../extensibility/internals/extending-the-object-model-of-the-base-project.md).  
  
## Многоуровневый агрегат  
 Реализации подтипа проекта, которая создает программу\-оболочку подтип проекта более низком уровне, необходимо запрограммированным совместно, чтобы разрешить внутренний подтип проекта, чтобы работать правильно.  Список ответственностей программирования включает:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> реализация подтипа проекта, который создает внутренний подтип должны делегировать в программу\-оболочку  <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> реализация внутреннего подтипа для обоих проектов  <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> и  <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> методы.  
  
-   <xref:EnvDTE80.IInternalExtenderProvider> реализация подтипа проекта программы\-оболочки должен делегировать этому из своего внутреннего подтипа проекта.  В частности, реализации <xref:EnvDTE80.IInternalExtenderProvider.GetExtenderNames%2A> требуется получить строку имен из внутреннего подтипа проекта, а затем сцепления строк как он желает добавить расширителей.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> реализация подтипа программы\-оболочки создать экземпляр проекта  <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> объект внутреннего подтипа проекта и сохраняет его как закрытый делегат, поскольку только объект конфигурации проекта базового проекта непосредственно знает, что объект конфигурации подтипа проекта программы\-оболочки существует.  Внешний подтип проекта может изначально выбрать интерфейсы конфигурации его необходимо обрабатывать непосредственно, а затем остальные делегатов реализации внутреннего подтипа проекта <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg.get_CfgType%2A>.  
  
## Поддержка интерфейсов  
 Базовый проект вызовы делегатов, поддерживающий интерфейсы, добавленным подтипом данного проекта, чтобы расширить различные аспекты реализации.  Это включает расширение объекты конфигурации проекта, а также различные объекты обозревателя свойств.  Эти интерфейсы получены путем вызова `QueryInterface` на  `punkOuter` \(указатель  `IUnknown`\) внешней накопителя подтипа проекта.  
  
|Интерфейс|Подтип проекта|  
|---------------|--------------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>|Разрешает подтип проекта:<br /><br /> -   Предоставить реализацию метода <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>.<br />-   Мониторинг запуск отладчика, позволяя подтип проекта, чтобы предоставить свою собственную реализацию <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>.<br />-   Отключить вычисление выражений в процессе разработки автоматически обработка `DBGLAUNCH_DesignTimeExprEval` регистр в своей реализации  <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.QueryDebugLaunch%2A>.|  
|<xref:EnvDTE80.IInternalExtenderProvider>|Разрешает подтип проекта:<br /><br /> -   Расширение <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> добавление проекта или удалять свойства конфигурации независимые проекта.<br />-   Расширяет объект автоматизации проекта \(<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>\) проекта.<br /><br /> Значения свойств берутся из вышеуказанных <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> перечисление.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>|Разрешает подтип проекта для сопоставления обратно к <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> объект заданную конфигурацию проекта обзор объект.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBrowseObject>|Разрешает подтип проекта для сопоставления обратно к <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> или  `VSITEMID` объект, заданную конфигурацию проекта обзор объект.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>|Разрешает подтип проекта для сохранения произвольные структурированные данные XML в файл проекта \(с расширением vbproj или csproj\).  Эти данные скрыты в msbuild.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>|Разрешает подтип проекта:<br /><br /> -   Добавьте новые свойства msbuild для сохранения.<br />-   Удаление ненужных свойств msbuild.<br />-   Запрос для текущего значения свойства msbuild.<br />-   Измените текущее значение свойства msbuild.|  
  
## См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>