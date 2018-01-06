---
title: "Связанных служб и интерфейсов (VSPackage управления источника) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control packages, interfaces
- interfaces, source control packages
ms.assetid: 3e96e838-5675-46bb-99cf-40d420086038
caps.latest.revision: "26"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7d19c7e2560fafbf54257bf4c46303874bfc717b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="related-services-and-interfaces-source-control-vspackage"></a>Связанных служб и интерфейсов (VSPackage управления источника)
В этом разделе перечислены все интерфейсы, связанные с VSPackage в управления версиями [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]. Система управления версиями VSPackage реализует некоторые из этих интерфейсов и отчету другим пользователям для выполнения задач управления версиями.  
  
## <a name="interfaces-implemented-by-and-for-source-control-vspackages"></a>Интерфейсы, реализованные по, а также для пакетов VSPackage исходного элемента управления  
 Описываются следующие интерфейсы в [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], и системы управления версиями VSPackage реализует их часть в зависимости от набором требуемой функций. Некоторые интерфейсы помечаются как обязательный и должен быть реализован в каждой системе управления версиями пакета VSPackage.  
  
 Для этих интерфейсов, реализуемых пакета не [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] предоставляет реализацию по умолчанию. Обратите внимание, что реализация по умолчанию предназначен для в случае, когда регистрируется не VSPackage и проект не осуществляется. Неправильно написанный исходным VSPackage реализует все необходимые интерфейсы, но не оставляйте их реализации по умолчанию из этих интерфейсов.  
  
 Системы управления версиями VSPackage должен реализовывать закрытый служба, инкапсулирующая некоторые или все из следующих интерфейсов.  
  
 Интерфейсы являются:  
  
-   Требуется: Соответствующие сущности (проект системы управления версиями VSPackage, заглушка управления источника) должен реализовывать интерфейс.  
  
-   Рекомендуется: Сущности должны реализовывать этот интерфейс; в противном случае могут быть ограничены функций системы управления версиями.  
  
-   Необязательно: сущности можно реализовать этот интерфейс для обеспечения широким набором функций.  
  
|Интерфейс|Цель|Реализуемый|Реализовать?|  
|---------------|-------------|--------------------|----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|Редакторы вызывают этот интерфейс перед изменением или сохранение файла. Системы управления версиями VSPackage может извлечь этот файл или запретить операцию, если извлечение завершается ошибкой.|Система управления версиями VSPackage|Рекомендованное|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Этот интерфейс предоставляет основных функциях управления версиями для проектов, например регистрации и отмены регистрации проекты с системой управления версиями и поддержку управления глифы основные исходные.|Система управления версиями VSPackage|Обязательно|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Этот интерфейс можно получить из <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> с помощью <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> функция, или просто приведение объекта, реализующего `IVsHierarchy` для `IVsSccProject2`. Он используется для получения файлов в системе управления версиями в проекте или о том, текущее состояние системы управления версиями или расположение проекта.|Проект|Обязательно|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>|Модуль интеграции использует этот интерфейс для задания текущего активного VSPackage.|Система управления версиями VSPackage|Обязательно|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Этот интерфейс основан на модели подписки. Любой VSPackage можно указывают, что ему нужно получать события документа и знать о событиях, которые должны произойти, оболочкой. Реализуется и может быть обработано [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], в свою очередь, который передает события реализации `IVsTrackProjectDocumentsEvents2` в пакет VSPackage.|Заглушки исходного элемента управления|Обязательно|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3>|Этот интерфейс предоставляет пакетной обработки операций синхронизированные чтения и записи и расширенная `OnQueryAddFiles` метод.|Заглушки исходного элемента управления|Обязательно|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|**Обозреватель решений** и проекты вызывают этот интерфейс, при добавлении новых файлов в проектах или при файлов и папок, переименованы или удалены из проектов. Система управления версиями VSPackage можно извлечь файл проекта или отменить операцию.|Система управления версиями VSPackage|Рекомендованное|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3>|**Обозреватель решений** и проекты вызывают этот интерфейс в ответ на вызовы методов интерфейса IVstrackProjectDocuments3. Операций чтения и записи системы управления версиями, VSPackage может отслеживать пакетные операции, синхронизации и работать с более сложных `OnQueryAddFiles` метод.|Система управления версиями VSPackage|Рекомендованное|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation>|Этот интерфейс предоставляет управления прикрепление поддержка веб-проектов.|Система управления версиями VSPackage|Рекомендованное|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip>|Этот интерфейс используется для получения всплывающих подсказок для файлов с управлением версиями в проектах.|Система управления версиями VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl>|Этот интерфейс обеспечивает поддержку пространства имен расширения.|Система управления версиями VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution>|Пакет VSPackage использует этот интерфейс для интеграции расширение пространства имен в **New**, **откройте**, или **Сохранить** диалоговым окнам. Следовательно, проекты можно автоматически добавлены в систему управления версиями при создании или добавлены в систему управления версиями, во время сохранения действует операции.|Система управления версиями VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>|VSPackage использует этот интерфейс, чтобы определить дополнительные глифы как глифы управления источника для узлов в **обозревателе решений**.|Система управления версиями VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl>|**Добавить** диалоговое окно для веб-проектов использует этот интерфейс. Он предоставляет методы для просмотра расположение системы управления версиями, а также для открытия веб-проекта, ранее добавленных в репозитории системы управления версиями в этом расположении.|Система управления версиями VSPackage|Рекомендованное|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>|Этот интерфейс обеспечивает поддержку для асинхронного (фонового) загрузке проектов из системы управления версиями.|Система управления версиями VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents>|Этот интерфейс позволяет проектов для отслеживания хода выполнения асинхронной загрузки, инициированных <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>.|Проект|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions>|Этот интерфейс позволяет IDE, чтобы запросить VSPackage active систему управления версиями. IDE запрашивает значения параметров системы управления версиями, которые имеют значение даже в том случае, если элемент отсутствует активная исходная регистрации VSPackage. Этот интерфейс реализуется и может быть обработано [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].|Заглушки исходного элемента управления|Обязательно|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>|Этот интерфейс используется при регистрации VSPackage системы управления версиями.|Заглушки исходного элемента управления|Обязательно|  
|<xref:EnvDTE.SourceControl>|Этот интерфейс используется в службе автоматизации. Таким образом он предоставляет только те функции, которые могут выполняться без отображения пользовательского интерфейса.|Система управления версиями VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>|Этот интерфейс используется для сохранения параметров элемента управления источника в файле решения (SLN). Параметры включают расположение системы управления версиями и флаги состояния элемента управления источника.|Система управления версиями VSPackage|Рекомендованное|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>|Этот интерфейс используется для сохранения параметров системы управления версиями в файле параметров (.suo) решения. Сюда могут входить параметры системы управления версиями конкретного пользователя, таких как расположение прикрепление текущего пользователя.|Система управления версиями VSPackage|Рекомендованное|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>|Этот интерфейс используется для наблюдения за событиями для выполнения операций, таких как проверка в файлах проекта перед закрытием решения или получения новых файлов из системы управления версиями, при открытии проекта.|Система управления версиями VSPackage|Рекомендованное|  
  
## <a name="see-also"></a>См. также  
 [Элементы макета](../../extensibility/internals/source-control-vspackage-design-elements.md)