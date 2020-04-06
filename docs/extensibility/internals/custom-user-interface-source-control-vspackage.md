---
title: Пользовательский пользовательский интерфейс (Управление источником VSPackage) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interface, source control packages
- source control packages, user interface
ms.assetid: f35ddb24-53bf-461e-b34f-7414f657c082
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6ef807cef17a6ca3cddfee05ba57ace27e34a9e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708933"
---
# <a name="custom-user-interface-source-control-vspackage"></a>Пользовательский пользовательский интерфейс (управление исходным элементом VSPackage)
VSPackage объявляет свои элементы меню и состояния по умолчанию через таблицу команд Visual Studio (*.vsct)* файл. Интегрированная [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] среда разработки (IDE) отображает элементы меню в состояниях по умолчанию до загрузки VSPackage. Впоследствии <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метод вызывается для включения или отключать элементы меню.

 VSPackage может установить ключ реестра, чтобы VSPackage может быть автоматически загружен в зависимости от контекста пользовательского интерфейса команды (UI), хотя обычно управление исходным управлением VSPackage должно загружаться по требованию, а не просто переключаться на определенный контекст пользовательского интерфейса. Для получения дополнительной информации о ключе реестра **AutoLoadPackages** [см.](../../extensibility/managing-vspackages.md)

## <a name="vspackage-ui"></a>VSPackage UI
 Пакет управления исходным элементом реализован как VSPackage и [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]не использует какой-либо ui от . Каждый элемент управления исходного кода VSPackage должен указывать свои собственные элементы uI, такие как элементы меню, группы меню, окна инструментов, панели инструментов и любой необходимый uI для настройки параметров, специфиченных для управления исходом VSPackage. Эти элементы uI могут быть включены статично или динамически. Элементы static UI определяются в файле *.vsct* и отображаются независимо от того, загружается ЛИ VSPackage или нет. Динамические элементы uI могут быть видны в зависимости от конкретного контекста uI-вывода команд, <xref:EnvDTE.Constants.vsContextNoSolution>например, или в результате вызова к методу. <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Видимость динамических элементов uI соответствует стратегии задержки загрузки VSPackages.

## <a name="ui-constraints-on-source-control-vspackages"></a>Ограничения uI на элементуправления исходного элемента VSPackages
 Поскольку управление исходным элементом VSPackage не может быть удалено из IDE после его загрузки, VSPackage должен иметь возможность ввести неактивное состояние. Когда VSPackage получает уведомление о том, что он больше не активен, VSPackage отклоняет свой uI и игнорирует любое внешнее взаимодействие IDE. Реализация <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метода VSPackage должна скрывать команды, когда VSPackage не активен.

 Каждый элемент управления источником `IVsSccProvider` VSPackage должен реализовать интерфейс. Два метода на <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> интерфейсе, и <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>, должны быть реализованы VSPackage.

 Управление источником VSPackage, возможно, подписались на различные события <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>IDE, которые реализуются , и так далее. Кроме того, VSPackage, возможно, реализовал интерфейсы обратного <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>вызова с поддержкой реестра, такие как . Все эти интерфейсы должны быть проигнорированы, когда неактивны.

 В следующем списке показаны интерфейсы, затронутые активным состоянием управления исходным управлением VSPackage:

- Отслеживайте события проектной документации.

- События решения.

- Интерфейсы настойчивости решений. При неактивной неактивности пакеты не должны записываться в файлы *.sln* и *.suo.*

- Расширители свойств.

  <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> Требуемые <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>и, а также любые дополнительные интерфейсы, связанные с исходным управлением, не называются, когда управление исходным управлением VSPackage неактивен.

  При [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] запуске IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] устанавливает контекст мигов управления идентификатором текущего идентификатора исходного кода VSPackage ID. Это приводит к тому, что статический ui активного управления исходным элементом VSPackage появляется в IDE без фактической загрузки VSPackage. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]паузы для VSPackage, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] чтобы <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> зарегистрироваться через через до того, как он делает какие-либо звонки в VSPackage.

  В следующей таблице описаны [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] конкретные сведения о том, как IDE скрывает различные элементы uI.

| Элемент uI | Описание |
| - | - |
| Меню и панели инструментов | Пакет управления исходным элементом должен установить исходное меню и состояния видимости панели инструментов в идентификатор пакета управления исходным управлением в разделе [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) файла *.vsct.* Это позволяет [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE правильно устанавливать состояние элементов меню без загрузки VSPackage <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> и вызова реализации метода. |
| Окна инструментов | Управление исходным элементом VSPackage скрывает любые окна инструмента, которымонь он владеет, когда он сделан неактивным. |
| Страница вариантов управления исходным управлением VSPackage | Ключевой реестр **HKLM-SOFTWARE-Microsoft-VisualStudio-X.Y-ToolsOptionsPages/VisibilityCmdUIContexts** позволяет VSPackage установить контексты, в которых он требует его страниц вариантов для отображения. Запись реестра под этим ключом должна быть создана с помощью идентификатора службы (SID) службы управления исходным источником и присвоения ему значения DWORD 1. Всякий раз, когда событие uI происходит в контексте управления исходным управлением VSPackage зарегистрировано, VSPackage будет называться, если он активен. |

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>
- <xref:EnvDTE.Constants.vsContextNoSolution>
- [Управление пакетами VSPackage](../../extensibility/managing-vspackages.md)
