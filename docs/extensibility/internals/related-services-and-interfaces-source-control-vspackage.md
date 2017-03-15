---
title: "Связанные службы и интерфейсы (исходный элемент управления VSPackage) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control packages, interfaces
- interfaces, source control packages
ms.assetid: 3e96e838-5675-46bb-99cf-40d420086038
caps.latest.revision: 26
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
ms.openlocfilehash: 6d16e8eb229cd5187ae91630d9330a0e0f24eda2
ms.lasthandoff: 02/22/2017

---
# <a name="related-services-and-interfaces-source-control-vspackage"></a>Связанные службы и интерфейсы (VSPackage управления источника)
В этом разделе перечислены все интерфейсы в VSPackage управления версиями [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]. Системы управления версиями VSPackage реализует некоторые из этих интерфейсов и других использует для выполнения задач управления версиями.  
  
## <a name="interfaces-implemented-by-and-for-source-control-vspackages"></a>Интерфейсы, реализованные и для управления VSPackages источника  
 Следующие интерфейсы описаны в [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], и система управления версиями VSPackage реализует их подмножество в зависимости от его требуемой функции набора. Некоторые интерфейсы помечаются как обязательный и должен быть реализован в каждом VSPackage системы управления версиями.  
  
 Для этих интерфейсов, реализуемых пакета не [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] предоставляет реализацию по умолчанию. Обратите внимание, что реализация по умолчанию предназначена для случая при регистрации не VSPackage и проект не контролируется. Неправильно написанный исходным VSPackage реализует все необходимые интерфейсы, но не оставляйте их реализации по умолчанию этих интерфейсов.  
  
 Система управления версиями VSPackage необходимо реализовать частной службы, включающий в себя некоторые или все из следующих интерфейсов.  
  
 Интерфейсы являются:  
  
-   Требуется: Соответствующую сущность (проект системы управления версиями VSPackage, заглушка управления источника) необходимо реализовать интерфейс.  
  
-   Рекомендуется: Сущности должны реализовывать этот интерфейс; в противном случае могут быть ограничены функции системы управления версиями.  
  
-   Необязательно: сущности можно реализовать этот интерфейс для обеспечения широким набором функций.  
  
|Интерфейс|Назначение|Реализуется|Реализовать?|  
|---------------|-------------|--------------------|----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2></xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|Редакторы вызывают этот интерфейс перед изменением или сохранение файла. Системы управления версиями VSPackage можно извлечь файл или запретить операцию, если извлечение оканчивается неудачей.|Система управления версиями VSPackage|Рекомендованное|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Этот интерфейс предоставляет основных функциях управления версиями для проектов, таких как регистрация и Отмена регистрации проектов с помощью системы управления версиями и предоставление поддержки для управления глифов базового источника.|Система управления версиями VSPackage|Обязательное|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Этот интерфейс получается из <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>с помощью <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A>функция, или просто приведение объекта, реализующего `IVsHierarchy` для `IVsSccProject2`.</xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Он используется для получения файлов в системе управления версиями в проекте или о том, текущее состояние системы управления версиями или расположение проекта.|Проект|Обязательное|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>|Модуль интеграции использует этот интерфейс для настройки текущего активного VSPackage.|Система управления версиями VSPackage|Обязательное|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2></xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Этот интерфейс основан на модели подписки. Любой VSPackage могут послужить ему получать события документа и рекомендуется оболочкой для событий, которые должны произойти. Реализуется и обрабатываются [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], который, в свою очередь, передает события реализация `IVsTrackProjectDocumentsEvents2` в VSPackage.|Заглушки источника элемента управления|Обязательное|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3></xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3>|Этот интерфейс предоставляет пакетной обработки операций синхронизированных чтения и записи и расширенная `OnQueryAddFiles` метод.|Заглушки источника элемента управления|Обязательное|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2></xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|**Обозреватель решений** и проекты вызывают этот интерфейс при добавлении новых файлов в проектах или при переименованы или удалены из проектов, файлов и папок. VSPackage системы управления версиями можно извлечь файл проекта или отменить операцию.|Система управления версиями VSPackage|Рекомендованное|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3></xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3>|**Обозреватель решений** и проекты вызывают этот интерфейс в ответ на вызовы методов интерфейса IVstrackProjectDocuments3. Операции чтения и записи системы управления версиями, VSPackage можно отслеживать пакетных операций, синхронизации и работать с более сложных `OnQueryAddFiles` метод.|Система управления версиями VSPackage|Рекомендованное|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation>|Этот интерфейс обеспечивает поддержку прикрепления управления для веб-проектов.|Система управления версиями VSPackage|Рекомендованное|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip>|Этот интерфейс используется для получения всплывающих подсказок для файлов с управлением версиями в проектах.|Система управления версиями VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl>|Этот интерфейс обеспечивает поддержку расширения пространства имен.|Система управления версиями VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution>|VSPackage использует этот интерфейс для интеграции расширения пространства имен в **New**, **откройте**, или **Сохранить** диалоговые окна. Таким образом, проекты можно автоматически добавлен в систему управления версиями при его создании, или добавить в систему управления версиями во время сохранения действует операции.|Система управления версиями VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>|VSPackage использует этот интерфейс, чтобы определить дополнительные глифы как глифы управления источника для узлов в **обозревателе решений**.|Система управления версиями VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl>|**Добавить** диалоговое окно для веб-проектов использует этот интерфейс. Он предоставляет методы для просмотра для расположение системы управления версиями и для открытия веб-проекта, ранее добавленные в репозитории системы управления версиями в этом расположении.|Система управления версиями VSPackage|Рекомендованное|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc></xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>|Этот интерфейс обеспечивает поддержку для асинхронного (фонового) загрузке проектов из системы управления версиями.|Система управления версиями VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents></xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents>|Этот интерфейс позволяет проекты для отслеживания хода выполнения асинхронной загрузки, инициированные <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>|Проект|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions>|Этот интерфейс позволяет интегрированной среды разработки для запроса VSPackage active системы управления версиями. IDE запрашивает значения параметров системы управления версиями, имеющие смысл даже в том случае, если элемент управления отсутствует активный источник зарегистрированного VSPackage. Этот интерфейс реализуется и обрабатываются [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].|Заглушки источника элемента управления|Обязательное|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider></xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>|Этот интерфейс используется в процессе регистрации VSPackage системы управления версиями.|Заглушки источника элемента управления|Обязательное|  
|<xref:EnvDTE.SourceControl></xref:EnvDTE.SourceControl>|Этот интерфейс используется в автоматизации. Таким образом он предоставляет только те функции, которые могут быть выполнены без отображения других элементов пользовательского интерфейса.|Система управления версиями VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps></xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>|Этот интерфейс используется для сохранения параметров элемента управления источником в файле решения (SLN). Параметры определяют расположение системы управления версиями и флаги состояния исходного элемента управления.|Система управления версиями VSPackage|Рекомендованное|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts></xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>|Этот интерфейс используется для сохранения параметров системы управления версиями в файле решения (.suo) параметры. Это может включать параметры системы управления версиями конкретного пользователя, такие как расположение прикрепление текущего пользователя.|Система управления версиями VSPackage|Рекомендованное|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3></xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>|Этот интерфейс используется для наблюдения за событиями для выполнения операций, например, для проверки в файлах проекта перед закрытием решения или получения новых файлов из системы управления версиями, при открытии проекта.|Система управления версиями VSPackage|Рекомендованное|  
  
## <a name="see-also"></a>См. также  
 [Элементы макета](../../extensibility/internals/source-control-vspackage-design-elements.md)
