---
title: "Пошаговое руководство: Добавление функции пользовательского редактора | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "редакторы [Visual Studio SDK] пользовательские - Добавление компонентов"
ms.assetid: bfe083b6-3e35-4b9c-ad4f-b30b9ff412a5
caps.latest.revision: 38
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 38
---
# Пошаговое руководство: Добавление функции пользовательского редактора
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

После создания пользовательского редактора, к нему можно добавить новые функции.  
  
### Чтобы создать редактор для VSPackage  
  
1.  Создание пользовательского редактора с помощью шаблона проекта пакета Visual Studio.  
  
     Дополнительные сведения см. в разделе [Пошаговое руководство: Создание специализированного редактора](../extensibility/walkthrough-creating-a-custom-editor.md).  
  
2.  Выбрать редактор для поддержки единого представления или несколько представлений.  
  
     Редактор, который поддерживает **новое окно** команды или имеет представление формы и представление кода, требуется отдельный документ объекты данных и объекты представления документа. В редакторе, который поддерживает только одно представление объект данных документа и объект представления документа может быть реализован на тот же объект.  
  
     Пример нескольких представлений в разделе [Поддерживает несколько представлений документов](../extensibility/supporting-multiple-document-views.md).  
  
3.  Реализуйте фабрику редактора путем реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> интерфейса.  
  
     Для получения дополнительной информации см. [Редактор фабрик](../extensibility/editor-factories.md).  
  
4.  Решите, должен редактора для использования активации на месте или упрощенного внедрения для управления объектом окна документа.  
  
     Окно редактора упрощенного внедрения размещает стандартном представлении документа, во время активации на месте окно редактора размещает элемент управления ActiveX или других активным объектом, как ее представление документа. Дополнительные сведения см. в разделах [Упрощенное внедрения](../extensibility/simplified-embedding.md) и [встроенная активация](../misc/in-place-activation.md).  
  
5.  Реализуйте <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейса для обработки команд.  
  
6.  Укажите сохранения документа и ответ на изменения внешнего файла следующим образом:  
  
    1.  Чтобы сохранить файл, реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> и <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> на свой редактор объект данных документа.  
  
    2.  Реагировать на изменения внешнего файла, реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> на свой редактор объект данных документа.  
  
        > [!NOTE]
        >  Вызов `QueryService` на <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx> может получить указатель на `IVsFileChangeEx`.  
  
7.  Координировать события редактирования документов с контролем исходного кода. Для этого:  
  
    1.  Получение указателя на `IVsQueryEditQuerySave2` путем вызова `QueryService` на <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>.  
  
    2.  При возникновении первой изменить событие, вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> метод.  
  
         Это пользователю будет предложено извлечь файл, если он еще не установлен. Убедитесь, что для обработки ошибок avert условие «файл не извлечен»  
  
    3.  Аналогичным образом, перед сохранением файла, вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> метод.  
  
         Этот метод предлагает пользователю сохранить файл, если он не был сохранен, или если он изменился с момента последнего сохранения.  
  
8.  Включить **Свойства** окно для отображения текста в редакторе свойств. Для этого:  
  
    1.  Вызов <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> каждый раз выделение текста изменяется, передав в своей реализации <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>.  
  
    2.  Вызов `QueryService` на <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> службы, чтобы получить указатель на <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>.  
  
9. Разрешить пользователям перетаскивать элементы между редактора и **элементов**, или между внешних редакторов \(например, Microsoft Word\) и **элементов**. Для этого:  
  
    1.  Реализация `IDropTarget` в редактор для создания предупреждения интегрированной среды разработки, что редактора объекта\-приемника.  
  
    2.  Реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> интерфейс для представления, можно включать и отключать элементы в редакторе **элементов**.  
  
    3.  Реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A> и вызвать `QueryService` на <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox> службы, чтобы получить указатель на <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> интерфейсов.  
  
         Это позволяет VSPackage для добавления новых элементов к **элементов**.  
  
10. Решите, следует ли дополнительные функции для редактора.  
  
    -   Если редактора для поддержки поиска и замены, реализовать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>.  
  
    -   Если вы хотите использовать средство окно структуры документа в редакторе, реализовать `IVsDocOutlineProvider`.  
  
    -   Если вы хотите использовать строку состояния в редакторе, реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> и вызов `QueryService` для <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> для получения указателя на `IVsStatusBar`.  
  
         Например, редактор может отображать строки и сведения о столбце, режим выбора \(потока \/ поле\) и режим вставки \(insert \/ overstrike\).  
  
    -   Если требуется редактора для поддержки `Undo` команд, рекомендуется использовать модель диспетчер отмены OLE. В качестве альтернативы, вы получаете дескриптор редактор `Undo` команды напрямую.  
  
11. Создание реестра сведения, включая идентификаторы GUID для VSPackage, меню, редактора и других функций.  
  
     Ниже приведен общий пример будет поместить в файл .rgs сценария для демонстрации правильной регистрации редактора кода.  
  
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
  
12. Реализация поддержки контекстной справки.  
  
     Это позволяет обеспечить поддержку справки F1 и динамической справки окна элементов в редакторе. Дополнительные сведения см. в разделе [Практическое руководство: предоставляют контекст для редакторов](../Topic/How%20to:%20Provide%20Context%20for%20Editors.md).  
  
13. Предоставление объектной модели автоматизации из редактора, реализовав `IDispatch` интерфейса.  
  
     Для получения дополнительной информации см. [Способствовали модели автоматизации](../extensibility/internals/contributing-to-the-automation-model.md).  
  
## Отказоустойчивость  
  
-   При вызове интегрированной среды разработки, создается экземпляр редактора <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> метод. Если редактор поддерживает несколько представлений `CreateEditorInstance` создает документ данных и объекты представления документа. Если объект данных документ уже открыть, отличных от null `punkDocDataExisting` передается значение `IVsEditorFactory::CreateEditorInstance`. Реализации фабрики редактора необходимо определить, совместима ли существующий объект данных документа, запрашивая соответствующие интерфейсы на нем. Для получения дополнительной информации см. [Поддерживает несколько представлений документов](../extensibility/supporting-multiple-document-views.md).  
  
-   При использовании упрощенный подход внедрения реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> интерфейса.  
  
-   Если вы решите использовать активацию на месте, реализуйте следующие интерфейсы:  
  
     <xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>  
  
     <xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>  
  
    > [!NOTE]
    >  `IOleInPlaceComponent` Интерфейс используется для предотвращения OLE 2 слияние меню.  
  
     Ваш `IOleCommandTarget` реализация обрабатывает команды, такие как **Вырезать**, **копирования**, и **Вставить**. При реализации `IOleCommandTarget`, решите, требуется ли редактора свой собственный файл .vsct для определения структуры меню собственную команду или если он может реализовать стандартных команд, определенных в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Как правило редакторы использовать и расширять меню интегрированной среды разработки и определить свои собственные панели инструментов. Тем не менее часто бывает для редактора определить свои собственные определенные команды наряду с использованием набора стандартных команд интегрированной среды разработки. Для этого редактора необходимо объявить стандартных команд, он использует и затем определить новые команды, контекстные меню, меню верхнего уровня и панели инструментов в файл .vsct. При создании активации на месте редактора, затем реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> и определить меню и панели инструментов редактора в файл .vsct вместо OLE 2 слияние меню.  
  
-   Для предотвращения команды меню в пользовательском Интерфейсе как правило, следует использовать существующие команды в Интегрированной среде разработки до изобретать новые команды. Общие команды определяются в SharedCmdDef.vsct и ShellCmdDef.vsct. Эти файлы устанавливаются по умолчанию в подкаталоге VisualStudioIntegration\\Common\\Inc вашей [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] установки.  
  
-   `ISelectionContainer` можно выразить одного или нескольких выбранных элементов. Каждый выбранный объект реализуется как `IDispatch` объект.  
  
-   Реализует IDE `IOleUndoManager` как службы, доступные из <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> или объектом, который может быть создан через <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>. Ваш редактор реализует `IOleUndoUnit` интерфейс для каждого `Undo` действие.  
  
-   Есть два места пользовательского редактора можно предоставить объекты автоматизации:  
  
    -   `Document.Object`  
  
    -   `Window.Object`  
  
## См. также  
 [Способствовали модели автоматизации](../extensibility/internals/contributing-to-the-automation-model.md)   
 [Практическое руководство: предоставляют контекст для редакторов](../Topic/How%20to:%20Provide%20Context%20for%20Editors.md)