---
title: Пошаговое руководство. Добавление компонентов в пользовательский редактор | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - add features
ms.assetid: bfe083b6-3e35-4b9c-ad4f-b30b9ff412a5
caps.latest.revision: 39
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1d14fb36298518409df34302f9346e186f0b0263
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "67825167"
---
# <a name="walkthrough-adding-features-to-a-custom-editor"></a>Пошаговое руководство. Добавление функций в специализированный редактор
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

После создания пользовательского редактора к нему можно добавить дополнительные компоненты.  
  
### <a name="to-create-an-editor-for-a-vspackage"></a>Создание редактора для VSPackage  
  
1. Создайте пользовательский редактор с помощью шаблона проекта пакета Visual Studio.  
  
     Дополнительные сведения см. [в разделе Пошаговое руководство. Создание пользовательского редактора](../extensibility/walkthrough-creating-a-custom-editor.md).  
  
2. Решите, должен ли редактор поддерживать одно или несколько представлений.  
  
     Редактор, поддерживающий команду " **создать окно** " или имеющий представление формы и кода, требует наличия отдельных объектов данных документа и объектов представления документов. В редакторе, поддерживающем только одно представление, объект данных документа и объект представления документа могут быть реализованы в одном и том же объекте.  
  
     Пример нескольких представлений см. в разделе [Поддержка нескольких представлений документов](../extensibility/supporting-multiple-document-views.md).  
  
3. Реализуйте фабрику редактора, реализовав <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> интерфейс.  
  
     Дополнительные сведения см. в разделе [фабрики редактора](../extensibility/editor-factories.md).  
  
4. Решите, должен ли редактор использовать активацию на месте или упрощенное внедрение для управления окном объекта представления документов.  
  
     В упрощенном окне редактора внедрено стандартное представление документа, в то время как в окне редактора активации на месте в качестве представления документа размещается элемент управления ActiveX или другой активный объект. Дополнительные сведения см. в разделе [упрощенное внедрение](../extensibility/simplified-embedding.md) и [Активация на месте](../misc/in-place-activation.md).  
  
5. Реализуйте <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс для обработки команд.  
  
6. Предоставьте сохраняемость документов и отклики на изменения внешних файлов, выполнив следующие действия.  
  
    1. Чтобы сохранить файл, реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> и <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> в объекте данных документа редактора.  
  
    2. Для реагирования на изменения внешних файлов, реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> в объекте данных документа редактора.  
  
        > [!NOTE]
        > Вызовите `QueryService` On <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx> , чтобы получить указатель на `IVsFileChangeEx` .  
  
7. Координация событий изменения документа с помощью системы управления исходным кодом. Для этого выполните следующие действия.  
  
    1. Получите указатель на `IVsQueryEditQuerySave2` , вызвав `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> .  
  
    2. При возникновении первого события изменения вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> метод.  
  
         При этом пользователю предлагается извлечь файл, если он еще не извлечен. Не забудьте обрабатывать условие "файл не извлечен" для AVERT ошибок  
  
    3. Аналогично, перед сохранением файла вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> метод.  
  
         Этот метод предлагает пользователю сохранить файл, если он не был сохранен или был изменен с момента последнего сохранения.  
  
8. Включите окно " **Свойства** ", чтобы отобразить свойства для текста, выбранного в редакторе. Для этого выполните следующие действия.  
  
    1. Вызывайте <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> каждый раз при изменении выбора текста, передавая реализацию <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> .  
  
    2. Вызовите `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> службу, чтобы получить указатель на <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> .  
  
9. Разрешить пользователям перетаскивать элементы между редактором и **панелью элементов**, а также между внешними редакторами (например, Microsoft Word) и **панелью элементов**. Для этого выполните следующие действия.  
  
    1. Реализуйте `IDropTarget` в редакторе, чтобы предупредить интегрированную среду разработки о том, что редактор является целью перетаскивания.  
  
    2. Реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> интерфейс в представлении, чтобы редактор мог включать и отключать элементы на **панели элементов**.  
  
    3. Реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A> интерфейс и вызовите `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox> службу, чтобы получить указатель <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> на <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> интерфейсы и.  
  
         Это позволяет пакету VSPackage добавлять новые элементы на **панель элементов**.  
  
10. Решите, хотите ли вы использовать другие дополнительные функции для редактора.  
  
    - Если вы хотите, чтобы редактор поддерживал команды Find и Replace, реализуйте <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget> .  
  
    - Если вы хотите использовать в редакторе окно инструментов структуры документа, реализуйте `IVsDocOutlineProvider` .  
  
    - Если вы хотите использовать строку состояния в редакторе, реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> и вызовите метод `QueryService` для <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> получения указателя на `IVsStatusBar` .  
  
         Например, редактор может отображать сведения о строках и столбцах, режим выделения (поток/поле) и режим вставки (INSERT/зачеркнутый).  
  
    - Если требуется, чтобы редактор поддерживал `Undo` команду, рекомендуется использовать модель ДИСПЕТЧЕРА OLE-отмены. В качестве альтернативы можно сделать так, чтобы редактор обрабатывал `Undo` команду напрямую.  
  
11. Создайте данные реестра, включая идентификаторы GUID для VSPackage, меню, редактор и другие функции.  
  
     Ниже приведен общий пример кода, который можно разместить в скрипте. RGS-файла, чтобы продемонстрировать, как правильно зарегистрировать редактор.  
  
    ```  
    NoRemove Editors  
    {  
          ForceRemove {...guidEditor...} = s 'RTF Editor'  
          {  
             val Package = s '{...guidVsPackage...}'  
             ForceRemove Extensions  
             {  
                val rtf = d 50  
             }  
          }  
    }  
    NoRemove Menus  
    {  
          val {...guidVsPackage...} = s ',203,11'  
    }  
    ```  
  
12. Реализация поддержки контекстно-зависимой справки.  
  
     Это позволяет предоставить справку F1 и поддержку окна динамической справки для элементов в редакторе. Дополнительные сведения об этом см. [в разделе руководство. Предоставление контекста для редакторов](../extensibility/how-to-provide-context-for-editors.md).  
  
13. Предоставьте объектную модель автоматизации из редактора, реализовав `IDispatch` интерфейс.  
  
     Для получения дополнительной информации см. [Contributing to the Automation Model](../extensibility/internals/contributing-to-the-automation-model.md).  
  
## <a name="robust-programming"></a>Отказоустойчивость  
  
- Экземпляр редактора создается, когда интегрированная среда разработки вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> метод. Если редактор поддерживает несколько представлений, `CreateEditorInstance` создает как данные документа, так и объекты представления документов. Если объект данных документа уже открыт, `punkDocDataExisting` передается значение, отличное от NULL `IVsEditorFactory::CreateEditorInstance` . Реализация фабрики редактора должна определить, совместим ли существующий объект данных документа, путем запроса соответствующих интерфейсов. Дополнительные сведения см. в разделе [Поддержка нескольких представлений документов](../extensibility/supporting-multiple-document-views.md).  
  
- Если используется упрощенный подход к внедрению, реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> интерфейс.  
  
- Если вы решили использовать активацию на месте, реализуйте следующие интерфейсы:  
  
     <xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>  
  
     <xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>  
  
    > [!NOTE]
    > `IOleInPlaceComponent`Интерфейс используется, чтобы избежать слияния меню OLE 2.  
  
     Ваша `IOleCommandTarget` реализация обрабатывает команды, такие как **вырезание**, **копирование**и **Вставка**. При реализации `IOleCommandTarget` решите, требуется ли редактору собственный файл. vsct, чтобы определить собственную структуру меню команд или, если она может реализовывать стандартные команды, определенные [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Обычно редакторы используют и расширяют меню интегрированной среды разработки и определяют собственные панели инструментов. Однако часто бывает необходимо, чтобы редактор определял собственные конкретные команды в дополнение к использованию стандартного набора команд интегрированной среды разработки. Для этого редактор должен объявить стандартные команды, которые он использует, а затем определить новые команды, контекстные меню, меню верхнего уровня и панели инструментов в vsct-файле. Если вы создаете редактор активации на месте, то реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> и определите меню и панели инструментов для редактора в vsct-файле, а не слияние меню с OLE 2.  
  
- Чтобы команда меню кровдинг в пользовательском интерфейсе, следует использовать существующие команды в интегрированной среде разработки перед созданием новых команд. Общие команды определяются в Шаредкмддеф. vsct и Шеллкмддеф. vsct. Эти файлы устанавливаются по умолчанию в подкаталог Висуалстудиоинтегратион\коммон\инк [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] установки.  
  
- `ISelectionContainer` может выражать как один, так и несколько элементов. Каждый выбранный объект реализуется как `IDispatch` объект.  
  
- Интегрированная среда разработки реализует `IOleUndoManager` как службу, доступную из, <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> или как объект, экземпляр которого можно создать с помощью <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> . Редактор реализует `IOleUndoUnit` интерфейс для каждого `Undo` действия.  
  
- Существует два места, в которых пользовательский редактор может предоставлять объекты автоматизации:  
  
  - `Document.Object`  

  - `Window.Object`  
  
## <a name="see-also"></a>См. также:  
 [Вклад в модель автоматизации](../extensibility/internals/contributing-to-the-automation-model.md)   
 [Практическое руководство. Предоставление контекста для редакторов](../extensibility/how-to-provide-context-for-editors.md)
