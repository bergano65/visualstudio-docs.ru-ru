---
title: "Пользовательский интерфейс (исходный элемент управления VSPackage) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user interface, source control packages
- source control packages, user interface
ms.assetid: f35ddb24-53bf-461e-b34f-7414f657c082
caps.latest.revision: 28
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
ms.openlocfilehash: 0d4940ea62ac65671ffcb3bb29958e3d2e544c09
ms.lasthandoff: 02/22/2017

---
# <a name="custom-user-interface-source-control-vspackage"></a>Пользовательский интерфейс (VSPackage управления источника)
VSPackage объявляет элементами меню и состояние по умолчанию в файле таблицы команд Visual Studio (.vsct). [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Интегрированной среды разработки (IDE) отображает элементы меню в состояние по умолчанию до загрузки VSPackage. Следовательно <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>метод вызывается для включения или отключения элементов меню.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>  
  
 VSPackage можно задать раздел реестра, поэтому VSPackage автоматически загружается в зависимости от того, пользовательский интерфейс (UI) команда контекст, хотя обычно из системы управления версиями VSPackage следует загружать по требованию, а не просто переключение к определенному контексту пользовательского интерфейса. Дополнительные сведения о разделе реестра AutoLoadPackages см. в разделе [управление VSPackages](../../extensibility/managing-vspackages.md).  
  
## <a name="vspackage-ui"></a>Пользовательский Интерфейс VSPackage  
 Пакет управления версиями реализуется как VSPackage и не использует никаких элементов пользовательского интерфейса из [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Каждый VSPackage системы управления версиями необходимо указать собственные элементы пользовательского интерфейса, например пунктов меню, группы меню, окна инструментов, панели инструментов и других необходимых элементов пользовательского интерфейса для настройки определенных параметров в систему управления версиями VSPackage. Можно включить эти элементы пользовательского интерфейса статически или динамически. Статические элементы пользовательского интерфейса определены в файле .vsct и отображаются ли загрузки VSPackage или нет. Динамические элементы пользовательского интерфейса могут быть видны в зависимости от конкретной команды контекст пользовательского интерфейса, такие как <xref:EnvDTE.Constants.vsContextNoSolution>, или в результате вызова <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>метод.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> </xref:EnvDTE.Constants.vsContextNoSolution> Видимость динамические элементы пользовательского интерфейса соответствует стратегии для отложенной загрузки пакетов VSPackages.  
  
## <a name="ui-constraints-on-source-control-vspackages"></a>Ограничения VSPackages исходного элемента управления пользовательского интерфейса  
 VSPackage системы управления версиями не удаляются из интегрированной среды разработки, после его загрузки, необходимо иметь возможность вводить в неактивное состояние VSPackage. VSPackage, получив уведомление больше не является активным, VSPackage отключает пользовательский Интерфейс и игнорирует любые внешнего взаимодействия IDE. Реализация VSPackage <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>метода следует скрыть команды, когда VSPackage неактивен.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>  
  
 Каждый элемент управления источника, необходимо реализовать VSPackage `IVsSccProvider` интерфейса. Два метода в интерфейсе, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A>и <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>, должен быть реализован в VSPackage.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A>  
  
 Система управления версиями VSPackage могут подписываться на различные события интегрированной среды разработки, реализованных <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>и т.д.</xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> </xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> Кроме того VSPackage может реализовывать интерфейсы обратного вызова с поддержкой реестра, такие как <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> Они должны все игнорироваться неактивная.  
  
 Ниже перечислены интерфейсы, затронутых активное состояние системы управления версиями VSPackage.  
  
-   Отслеживать события документы проекта.  
  
-   События решения.  
  
-   Интерфейсы сохранения решения. Неактивная, пакеты не должен записывать файлы SLN и SUO.  
  
-   Свойство расширителей.  
  
 Обязательный <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>и <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>, а также любые дополнительные интерфейсы, связанные с системой управления версиями, не вызываются, если система управления версиями VSPackage неактивна.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> </xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>  
  
 Когда [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] запуске интегрированной среды разработки, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] задает контекст команды пользовательского интерфейса на идентификатор текущего управления версиями по умолчанию идентификатор VSPackage. В результате статического пользовательского интерфейса элемента управления активной исходной VSPackage могут появляться в Интегрированной среде разработки без фактической загрузки VSPackage. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Приостанавливает на VSPackage для регистрации [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] через <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>перед отправкой любые вызовы VSPackage.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>  
  
 В следующей таблице описаны конкретные сведения о том, как [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE скрывает различных элементов пользовательского интерфейса.  
  
|Элемент пользовательского интерфейса|Описание|  
|-------------|-----------------|  
|Меню и панели инструментов|Пакет системы управления версиями необходимо задать начальное состояние видимости меню и панель инструментов идентификатора исходного пакета в [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) файла .vsct. Это позволяет [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки, чтобы соответствующим образом задать состояние пунктов меню без загрузки VSPackage и вызова реализации <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>метод.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>|  
|Окна инструментов|Система управления версиями VSPackage скрывает все окна инструментов, которыми он владеет, когда он становится неактивным.|  
|Страницы параметров системы управления версиями конкретного VSPackage|Раздел реестра HKLM\SOFTWARE\Microsoft\VisualStudio\X.Y\ToolsOptionsPages\VisibilityCmdUIContexts позволяет задать контексты, в которых требуется его параметры страницы для отображения VSPackage. Запись реестра в этом разделе должны создаваться с помощью службы ИД службы управления источника и назначения его значение DWORD, равное 1. Каждый раз, когда событие пользовательского интерфейса происходит в контексте системы управления версиями, с зарегистрированного VSPackage, VSPackage будет вызываться активна.|  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A></xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2></xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider></xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>   
 <xref:EnvDTE.Constants.vsContextNoSolution></xref:EnvDTE.Constants.vsContextNoSolution>   
 [Управление пакеты VSPackage](../../extensibility/managing-vspackages.md)
