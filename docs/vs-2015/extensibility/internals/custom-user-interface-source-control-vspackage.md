---
title: Настраиваемый пользовательский интерфейс (пакет VSPackage управления версиями) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- user interface, source control packages
- source control packages, user interface
ms.assetid: f35ddb24-53bf-461e-b34f-7414f657c082
caps.latest.revision: 29
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f03713213ec2e54ed8d82d7528dae12cefab7ebc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68154977"
---
# <a name="custom-user-interface-source-control-vspackage"></a>Настраиваемый пользовательский интерфейс (пакет VSPackage системы управления версиями)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

VSPackage объявляет элементами меню и состояние по умолчанию в файле Visual Studio Command Table (.vsct). [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Интегрированной среды разработки (IDE) отображается пунктов меню в состояние по умолчанию, пока не загружается VSPackage. Как следствие <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метод вызывается для включения или отключения пунктов меню.  
  
 VSPackage может задать раздел реестра, чтобы пакет VSPackage может загружаться автоматически в зависимости от контекста команд пользовательского интерфейса пользователя, несмотря на то, что обычно системы управления версиями по запросу, а не просто переключая таблицы к конкретному контексту пользовательского интерфейса должен загрузиться проект VSPackage. Дополнительные сведения о разделе реестра AutoLoadPackages см. в разделе [пакеты VSPackage, управление](../../extensibility/managing-vspackages.md).  
  
## <a name="vspackage-ui"></a>Пользовательский Интерфейс VSPackage  
 Пакет системы управления версиями реализуется в виде пакета VSPackage и пользовательского интерфейса, из которой не используются [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Каждый пакет VSPackage системы управления версиями необходимо указать свои собственные элементы пользовательского интерфейса, такие как элементы меню, группы меню, окна инструментов, панели инструментов и пользовательского интерфейса, необходимые для установки определенных параметров для пакета VSPackage системы управления версиями. Эти элементы пользовательского интерфейса можно включить статически или динамически. Статические элементы пользовательского интерфейса определяются в vsct-файл и отображаются ли или не загружается VSPackage. Динамические элементы пользовательского интерфейса могут быть видны в зависимости от конкретной команды контекст пользовательского интерфейса, такие как <xref:EnvDTE.Constants.vsContextNoSolution>, или в результате вызова <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метод. Видимость динамические элементы пользовательского интерфейса соответствует стратегии для отложенной загрузки пакетов VSPackage.  
  
## <a name="ui-constraints-on-source-control-vspackages"></a>Ограничения пользовательского интерфейса на пакетом VSPackage системы управления источника  
 Так как пакет VSPackage системы управления версиями невозможно удалить из интегрированной среды разработки, после ее загрузки, VSPackage должен быть может перейти в неактивном состоянии. Получив уведомление, что он более не активен, VSPackage VSPackage отключает пользовательский Интерфейс и игнорирует любого внешнего взаимодействия интегрированной среды разработки. Реализацию VSPackage <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метод следует скрыть команды, если пакет VSPackage не активен.  
  
 Системы управления версиями, каждый пакет VSPackage должен реализовывать `IVsSccProvider` интерфейс. Два метода в интерфейсе, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>, должен быть реализован в VSPackage.  
  
 Системы управления версиями, VSPackage могут подписываться на различные события интегрированной среды разработки, которые реализуются с <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>, и т. д. Кроме того, пакет VSPackage может реализовывать интерфейсы с поддержкой реестра обратного вызова, такие как <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>. Они все не следует учитывать при неактивной.  
  
 В следующем списке приведены интерфейсы, затронутых активное состояние пакета VSPackage системы управления версиями:  
  
- Отслеживать событиях документов проекта.  
  
- Событиях решения.  
  
- Интерфейсы сохраняемости решения. Неактивная, пакеты не должен записывать файлы SLN и SUO.  
  
- Свойство средства расширения.  
  
  Необходимая <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>, а также любые дополнительные интерфейсы, связанные с системой управления версиями, не вызываются, когда пакет VSPackage системы управления версиями является неактивным.  
  
  Когда [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] запускает интегрированную среду разработки, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] задает контекст команды пользовательского интерфейса с идентификатором текущего управления версиями по умолчанию идентификатор пакета VSPackage. В результате статического пользовательского интерфейса элемента управления активной исходной VSPackage отображаются в интегрированной среде разработки без фактической загрузки VSPackage. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Приостанавливает для VSPackage для регистрации в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] через <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> перед отправкой каких-либо вызовов VSPackage.  
  
  В следующей таблице описаны конкретные сведения о том, как [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE скрывает различных элементов пользовательского интерфейса.  
  
|Элемент пользовательского интерфейса|Описание|  
|-------------|-----------------|  
|Меню и панели инструментов|Пакет системы управления версиями необходимо задать начальное состояние видимости меню и панель инструментов идентификатора источника пакета в [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) раздел файла .vsct. Это позволяет [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] интегрированной среды разработки для задания состояния пунктов меню, соответствующим образом без загрузки VSPackage и вызова реализации <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метод.|  
|Окна инструментов|Пакет VSPackage системы управления версиями скрывает все окна инструментов, которыми он владеет, когда он становится неактивным.|  
|Страницы параметров системы управления версиями определенного VSPackage|Раздел реестра HKLM\SOFTWARE\Microsoft\VisualStudio\X.Y\ToolsOptionsPages\VisibilityCmdUIContexts позволяет задавать контексты, в которых требуется его параметры страницы, которые будут отображаться VSPackage. Запись реестра, в этом разделе необходимо создать с помощью службы идентификатора (SID) службы управления версиями и назначив ей значение DWORD, равное 1. Каждый раз, когда событие пользовательского интерфейса находится в контексте, который пакет VSPackage зарегистрирован с помощью системы управления версиями, VSPackage будет вызываться, если он активен.|  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>   
 <xref:EnvDTE.Constants.vsContextNoSolution>   
 [Управление пакетами VSPackage](../../extensibility/managing-vspackages.md)
