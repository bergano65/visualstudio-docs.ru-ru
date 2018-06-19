---
title: Настраиваемый пользовательский интерфейс (VSPackage управления источника) | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- user interface, source control packages
- source control packages, user interface
ms.assetid: f35ddb24-53bf-461e-b34f-7414f657c082
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ebd2361e94e9b1430f5bac99f2e71dc53a02ebf1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131891"
---
# <a name="custom-user-interface-source-control-vspackage"></a>Настраиваемый пользовательский интерфейс (VSPackage управления источника)
VSPackage объявляет элементами меню и состояние по умолчанию, файл таблицы команд Visual Studio (.vsct). [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Интегрированной среды разработки (IDE) будет отображаться элементы меню в состояние по умолчанию загружается пакет VSPackage. Впоследствии <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метод вызывается для включения или отключения пунктов меню.  
  
 VSPackage может задать раздел реестра, поэтому VSPackage автоматически загружается в зависимости от того, пользовательский интерфейс (UI) команда контекст, несмотря на то, что обычно системы управления версиями пакета VSPackage следует загружать по требованию, а не просто переключения для определенного контекста пользовательского интерфейса. Дополнительные сведения о разделе реестра AutoLoadPackages см. в разделе [управления пакеты VSPackage](../../extensibility/managing-vspackages.md).  
  
## <a name="vspackage-ui"></a>VSPackage пользовательского интерфейса  
 Пакет системы управления версиями реализуется как VSPackage и не использует никаких элементов пользовательского интерфейса из [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Каждый пакет VSPackage системы управления версиями необходимо указать свои собственные элементы пользовательского интерфейса, такие как элементы меню, группы меню, окна инструментов, панели инструментов и пользовательского интерфейса, необходимые для установки конкретных параметров в VSPackage систему управления версиями. Эти элементы пользовательского интерфейса можно включить статически или динамически. Статические элементы пользовательского интерфейса определяются в vsct-файл и отображаются ли VSPackage загружается или нет. Динамические элементы пользовательского интерфейса могут быть видны в зависимости от того, в контексте определенной команды пользовательского интерфейса, такие как <xref:EnvDTE.Constants.vsContextNoSolution>, или в результате вызова <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метод. Видимость динамических элементов пользовательского интерфейса, соответствует стратегии для отложенной загрузки пакетов VSPackage.  
  
## <a name="ui-constraints-on-source-control-vspackages"></a>Ограничения пакеты VSPackage исходного элемента управления пользовательского интерфейса  
 VSPackage системы управления версиями не удаляются из интегрированной среды разработки, после ее загрузки, VSPackage должен иметь возможность вводить неактивного состояния. Получив уведомление больше не является активной, VSPackage VSPackage отключает его пользовательского интерфейса и игнорирует какого-либо внешнего взаимодействия IDE. Реализация VSPackage <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метода следует скрыть команды, если пакет VSPackage не активен.  
  
 Каждой системы управления версиями, VSPackage должен реализовать `IVsSccProvider` интерфейса. Два метода в интерфейсе, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>, должен быть реализован в пакете VSPackage.  
  
 Система управления версиями, пакет VSPackage может подписаны на различные события интегрированной среды разработки, реализуемые с <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>, и т. д. Кроме того, пакет VSPackage может реализовывать интерфейсы поддержкой реестра обратного вызова, таких как <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>. Они все не следует учитывать неактивном состоянии.  
  
 Ниже перечислены интерфейсы, затронутых активное состояние системы управления версиями пакета VSPackage.  
  
-   Отслеживать события документы проекта.  
  
-   События решения.  
  
-   Интерфейсы сохраняемости решения. Неактивная, пакеты не должен записывать файлы SLN и SUO.  
  
-   Свойства расширения.  
  
 Необходимая <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>, а также любые дополнительные интерфейсы, связанные с системой управления версиями не вызываются, когда система управления версиями VSPackage неактивна.  
  
 Когда [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] запускает интегрированную среду разработки [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] задает контекст пользовательского интерфейса командной строки на идентификатор текущего управления версиями по умолчанию идентификатор пакета VSPackage. В этом случае статического пользовательского интерфейса элемента управления активной исходной VSPackage могут появляться в Интегрированной среде разработки без фактически загрузки VSPackage. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Приостанавливает для VSPackage для регистрации [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] через <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> перед отправкой каких-либо вызовов VSPackage.  
  
 В следующей таблице описаны конкретные сведения о том, как [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE скрывает различных элементов пользовательского интерфейса.  
  
|Элемент пользовательского интерфейса|Описание|  
|-------------|-----------------|  
|Меню и панели инструментов|Пакет системы управления версиями необходимо задать начальные состояния видимости меню и панель инструментов с ИД пакета управления источника в [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) раздел vsct-файле. Это позволяет [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE, чтобы правильно настроить состояние элементов меню без загрузки VSPackage и вызова реализации <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метод.|  
|Окна инструментов|Система управления версиями VSPackage скрывает все окна инструментов, которыми он владеет, когда становится неактивным.|  
|Страницы параметров системы управления версиями, зависящие от пакета VSPackage|Раздел реестра HKLM\SOFTWARE\Microsoft\VisualStudio\X.Y\ToolsOptionsPages\VisibilityCmdUIContexts позволяет задать контексты, в которых требуется его параметры страницы для отображения VSPackage. В этом разделе реестра бы создан с помощью службы ИД службы управления источника и назначения его значение DWORD, равное 1. Каждый пользовательский Интерфейс в контексте VSPackage, зарегистрированные с помощью системы управления версиями, пакет VSPackage будет вызываться при он остается активным.|  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>   
 <xref:EnvDTE.Constants.vsContextNoSolution>   
 [Управление пакетами VSPackage](../../extensibility/managing-vspackages.md)