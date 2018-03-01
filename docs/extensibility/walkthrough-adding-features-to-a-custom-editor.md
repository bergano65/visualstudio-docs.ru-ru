---
title: "Пошаговое руководство: Добавление функций специализированного редактора | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], custom - add features
ms.assetid: bfe083b6-3e35-4b9c-ad4f-b30b9ff412a5
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: f3c207b80686a66d9a06b8c50321b4dce2257ada
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-adding-features-to-a-custom-editor"></a>Пошаговое руководство: Добавление функций специализированного редактора
После создания пользовательского редактора, можно добавить дополнительные компоненты к нему.  
  
### <a name="to-create-an-editor-for-a-vspackage"></a>Чтобы создать редактор для VSPackage  
  
1.  Создание пользовательского редактора с помощью шаблона проекта пакета Visual Studio.  
  
     Дополнительные сведения см. в разделе [Пошаговое руководство: Создание специализированного редактора](../extensibility/walkthrough-creating-a-custom-editor.md).  
  
2.  Решите, будет ли редактора для поддержки представления один или несколько представлений.  
  
     Редактор, который поддерживает **новое окно** команды или имеет представление формы и представление кода, требуется отдельный документ данных объекты и объекты представлений документа. Объект данных документа и объект представления документа может осуществляться в редактор, который поддерживает только одно представление, на тот же объект.  
  
     Пример несколько представлений см. в разделе [поддержки нескольких представлений документа](../extensibility/supporting-multiple-document-views.md).  
  
3.  Реализуйте фабрику редактора путем реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> интерфейса.  
  
     Дополнительные сведения см. в разделе [фабрик редакторов](../extensibility/editor-factories.md).  
  
4.  Определитесь, ваш редактор активации на месте или упрощенное внедрения для управления окна объекта представления документа.  
  
     Упрощенная внедрения окно редактора размещаются представления стандартный документ, тогда окно редактора встроенной активации содержит элемент управления ActiveX или другие активного объекта, как его представление документа. Дополнительные сведения см. в разделе [упрощенное внедрение](../extensibility/simplified-embedding.md) и [встроенной активации](../extensibility/in-place-activation.md).  
  
5.  Реализуйте <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейса для обработки команд.  
  
6.  Укажите сохраняемость документа и ответ на изменения внешнего файла следующим образом:  
  
    1.  Чтобы сохранить файл, реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> и <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> на объект данных документа в редакторе.  
  
    2.  Чтобы реагировать на изменения внешнего файла, реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> на объект данных документа в редакторе.  
  
        > [!NOTE]
        >  Вызовите `QueryService` на <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx> для получения указателя на `IVsFileChangeEx`.  
  
7.  Координировать события изменения документа с контролем исходного кода. Для этого выполните следующие действия.  
  
    1.  Получение указателя на `IVsQueryEditQuerySave2` путем вызова `QueryService` на <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>.  
  
    2.  При возникновении первой изменить событие, вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> метод.  
  
         Пользователю, чтобы извлечь файл, если он не уже извлечен. Убедитесь, что для обработки условием «файл не извлечен», чтобы предотвратить ошибки  
  
    3.  Аналогичным образом, прежде чем сохранять файл, вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> метод.  
  
         Этот метод предлагает пользователю сохранить файл, если он не был сохранен, или если он был изменен с момента последнего сохранения.  
  
8.  Включить **свойства** окно для отображения свойств для текста, выделенного в редакторе. Для этого выполните следующие действия.  
  
    1.  Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> выделение текста каждый раз изменяется, передача в реализации <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>.  
  
    2.  Вызовите `QueryService` на <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> службы, чтобы получить указатель на <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>.  
  
9. Разрешить пользователям путем перетаскивания элементов между редактор и **элементов**, или между внешних редакторов (например, Microsoft Word) и **элементов**. Для этого выполните следующие действия.  
  
    1.  Реализуйте `IDropTarget` на редактора для создания предупреждения интегрированной среды разработки, ваш редактор будет конечного расположения сброса.  
  
    2.  Реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> интерфейс для представления, можно включать и отключать элементы редактора **элементов**.  
  
    3.  Реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A> и вызвать `QueryService` на <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox> службы, чтобы получить указатель на <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> интерфейсов.  
  
         Это позволяет VSPackage для добавления новых элементов к **элементов**.  
  
10. Решите, будет ли дополнительные функции для редактора.  
  
    -   Ваш редактор для поддержки поиска и замены, реализуйте <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>.  
  
    -   Если вы хотите использовать окно инструментов структуры документа в редакторе, реализовать `IVsDocOutlineProvider`.  
  
    -   Если вы хотите использовать строку состояния в редакторе, реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> и вызвать `QueryService` для <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> для получения указателя на `IVsStatusBar`.  
  
         Например, редактор можно отобразить строки и сведения о столбцах, режим выбора (поток / поле) и режим вставки (insert / замены).  
  
    -   Если требуется редактора для поддержки `Undo` команд, рекомендуется использовать модель диспетчер отмены OLE. Кроме того, может иметь дескриптор редактор `Undo` команд напрямую.  
  
11. Создание реестра сведения, включая идентификаторы GUID для пакета VSPackage, меню, редактор и другие функции.  
  
     Ниже приведен общий пример будет помещать в скрипте файла .rgs для демонстрации правильно регистрации редактора кода.  
  
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
  
     Это позволяет обеспечить поддержку справки F1 и динамической справки окна, для элементов в редакторе. Дополнительные сведения см. в разделе [как: предоставляют контекст для редакторов](../extensibility/how-to-provide-context-for-editors.md).  
  
13. Предоставляют объектную модель автоматизации из редактора путем реализации `IDispatch` интерфейса.  
  
     Дополнительные сведения см. в разделе [способствовали модели автоматизации](../extensibility/internals/contributing-to-the-automation-model.md).  
  
## <a name="robust-programming"></a>Отказоустойчивость  
  
-   Экземпляр редактора создается при вызове IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> метод. Если редактор поддерживает несколько представлений `CreateEditorInstance` создает данные документа и объекты представления документа. Если объект данных документа уже открыть, отличных от null `punkDocDataExisting` передается значение `IVsEditorFactory::CreateEditorInstance`. Реализации фабрики редактора необходимо определить, совместима ли существующий объект данных документа, запрашивая соответствующие интерфейсы на нем. Дополнительные сведения см. в разделе [поддержки нескольких представлений документа](../extensibility/supporting-multiple-document-views.md).  
  
-   При использовании упрощенный подход внедрения реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> интерфейса.  
  
-   Если вы решили использовать активацию на месте, необходимо реализуйте следующие интерфейсы:  
  
     <xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>  
  
     <xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>  
  
    > [!NOTE]
    >  `IOleInPlaceComponent` Интерфейс используется для предотвращения OLE 2 слияние меню.  
  
     Ваш `IOleCommandTarget` реализация обрабатывает команды, такие как **Вырезать**, **копирования**, и **вставить**. При реализации `IOleCommandTarget`, решите, требуется ли редактора свой собственный vsct-файл для определения структуры меню свои собственные команды или если он может реализовывать стандартных команд, определенных в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Как правило редакторы использовать и расширять меню IDE и определить собственные панели инструментов. Тем не менее часто бывает для редактора определить собственную определенные команды, наряду с использованием набора стандартных команд интегрированной среды разработки. Для этого редактора необходимо объявить стандартных команд, он использует, а затем определите новые команды, контекстные меню, меню верхнего уровня и панели инструментов в vsct-файле. При создании активации на месте редактора, затем реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> и определить меню и панели инструментов редактора в vsct-файле вместо использования OLE 2 слияние меню.  
  
-   Во избежание команды меню, как правило в пользовательском Интерфейсе перед изобретать новые команды следует использовать существующие команды в Интегрированной среде разработки. Общие команды определяются в SharedCmdDef.vsct и ShellCmdDef.vsct. Эти файлы устанавливаются по умолчанию в подкаталоге VisualStudioIntegration\Common\Inc вашей [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] установки.  
  
-   `ISelectionContainer`можно выразить одной или нескольких выбранных элементов. Каждого выбранного объекта реализуется в виде `IDispatch` объекта.  
  
-   IDE реализует `IOleUndoManager` как служба, доступны из <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> или объектом, который может быть создан посредством <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>. Ваш редактор реализует `IOleUndoUnit` интерфейс для каждого `Undo` действие.  
  
-   Есть два места объекты автоматизации можно предоставлять пользовательский редактор:  
  
    -   `Document.Object`  
  
    -   `Window.Object`  
  
## <a name="see-also"></a>См. также  
 [Дополнение к модели автоматизации](../extensibility/internals/contributing-to-the-automation-model.md)   
 [Как: предоставляют контекст для редакторов](../extensibility/how-to-provide-context-for-editors.md)