---
title: 'Пошаговое руководство: Добавление функций в специализированный редактор | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], custom - add features
ms.assetid: bfe083b6-3e35-4b9c-ad4f-b30b9ff412a5
caps.latest.revision: 39
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f7f0d7c79590c197b7c226fb2cb2841235049bb3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49283066"
---
# <a name="walkthrough-adding-features-to-a-custom-editor"></a>Пошаговое руководство. Добавление функций в специализированный редактор
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

После создания настраиваемого редактора, можно добавить дополнительные функции к нему.  
  
### <a name="to-create-an-editor-for-a-vspackage"></a>Чтобы создать редактор для VSPackage  
  
1.  Создание пользовательского редактора, используя шаблон проекта пакета Visual Studio.  
  
     Дополнительные сведения см. в разделе [Пошаговое руководство: Создание специализированного редактора](../extensibility/walkthrough-creating-a-custom-editor.md).  
  
2.  Решите, следует ли редактора для поддержки единое представление или несколько представлений.  
  
     В редакторе, поддерживающем **новое окно** команды или имеет представление формы и представление кода, требует отдельного документа объекты и объекты представления документа. В редакторе, который поддерживает только одно представление объект данных документа и объект представления документа могут быть реализованы на тот же объект.  
  
     Пример того, несколько представлений, см. в разделе [Supporting Multiple Document Views](../extensibility/supporting-multiple-document-views.md).  
  
3.  Реализуйте фабрику редактора, реализовав <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> интерфейс.  
  
     Дополнительные сведения см. в разделе [фабрики редакторов](../extensibility/editor-factories.md).  
  
4.  Определите, ли ваш редактор для использования встроенной активации, или упрощенное внедрение для управления окна объекта представления документа.  
  
     Упрощенное внедрение окно редактора размещает представления стандартного документа, а окно редактора встроенной активации размещает элемент управления ActiveX или другого активного объекта, как ее представление документа. Дополнительные сведения см. в разделе [упрощенное внедрение](../extensibility/simplified-embedding.md) и [встроенной активации](../misc/in-place-activation.md).  
  
5.  Реализуйте <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейса для обработки команд.  
  
6.  Укажите сохраняемость документа и ответ на изменения внешнего файла следующим образом:  
  
    1.  Чтобы сохранить файл, реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> и <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> на объект данных документа в редакторе.  
  
    2.  Чтобы реагировать на изменения внешнего файла, реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> на объект данных документа в редакторе.  
  
        > [!NOTE]
        >  Вызовите `QueryService` на <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx> получить указатель на `IVsFileChangeEx`.  
  
7.  Координируйте события редактирования документов с контролем исходного кода. Для этого выполните следующие действия.  
  
    1.  Получить указатель на `IVsQueryEditQuerySave2` путем вызова `QueryService` на <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>.  
  
    2.  Когда происходит первое событие редактирования, вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> метод.  
  
         Это предлагает пользователю извлечь файл, если он не уже извлечен. Убедитесь, что для обработки условие «файл не извлечен», чтобы избежать ошибок  
  
    3.  Аналогичным образом, прежде чем сохранить файл, вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> метод.  
  
         Этот метод предлагает пользователю сохранить файл, если он не был сохранен, или если он был изменен с момента последнего сохранения.  
  
8.  Включить **свойства** окно для отображения свойств для текста, выделенного в редакторе. Для этого выполните следующие действия.  
  
    1.  Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> выделение текста каждый раз изменяется, передав в реализации <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>.  
  
    2.  Вызовите `QueryService` на <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> службу для получения указателя на <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>.  
  
9. Разрешить пользователям перетаскивать элементы между редактором и **элементов**, или между внешних редакторов (например, Microsoft Word) и **элементов**. Для этого выполните следующие действия.  
  
    1.  Реализуйте `IDropTarget` на редактора для создания предупреждения интегрированной среды разработки, что редактора является целью перетаскивания.  
  
    2.  Реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> интерфейс для представления, поэтому редактора можно включать и отключать элементы в **элементов**.  
  
    3.  Реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A> и вызвать `QueryService` на <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox> службу для получения указателя на <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> интерфейсов.  
  
         Это позволяет VSPackage для добавления новых элементов к **элементов**.  
  
10. Решите, следует ли другие дополнительные возможности для редактора.  
  
    -   Если вы хотите, чтобы редактора для поддержки найти и заменить команды, реализовать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>.  
  
    -   Если вы хотите использовать окно инструментов структуры документа в редакторе, реализовать `IVsDocOutlineProvider`.  
  
    -   Если вы хотите использовать строку состояния в редакторе, реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> и вызвать `QueryService` для <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> получить указатель на `IVsStatusBar`.  
  
         Например, редактор можно отобразить строки и сведения о столбцах, режим выбора (потоковая передача / поле) и режим вставки (insert / overstrike).  
  
    -   Если вы хотите, чтобы редактора для поддержки `Undo` команды, рекомендуется использовать модель диспетчера отмены OLE. Кроме того, что дескриптор редактор `Undo` команду напрямую.  
  
11. Создание реестра сведения, включая идентификаторы GUID для пакета VSPackage, меню, редактора и другие функции.  
  
     Ниже приведен общий пример кода, что можно поместить в скрипте файл .rgs для демонстрации правильной регистрации редактора.  
  
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
  
     Это позволяет обеспечить поддержку справки F1 и динамической справки окна, для элементов в редакторе. Дополнительные сведения об этом см. в разделе [как: предоставляют контекст для редакторов](../extensibility/how-to-provide-context-for-editors.md).  
  
13. Предоставляют объектную модель автоматизации из редактора, реализовав `IDispatch` интерфейс.  
  
     Для получения дополнительной информации см. [Contributing to the Automation Model](../extensibility/internals/contributing-to-the-automation-model.md).  
  
## <a name="robust-programming"></a>Отказоустойчивость  
  
-   Экземпляр редактора создается в том случае, когда вызывает интегрированной среды разработки <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> метод. Если редактор поддерживает несколько представлений, `CreateEditorInstance` создает данные документа и объекты представления документа. Если объект данных документа уже открыть, отличный от null `punkDocDataExisting` значение передается `IVsEditorFactory::CreateEditorInstance`. Реализации фабрики редактора необходимо определить, совместима ли существующий объект данных документа, запрашивая соответствующие интерфейсы на нем. Дополнительные сведения см. в разделе [Supporting Multiple Document Views](../extensibility/supporting-multiple-document-views.md).  
  
-   Если вы используете упрощенный способ внедрения, реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> интерфейс.  
  
-   Если вы решили использовать активацию на месте, реализуйте следующие интерфейсы:  
  
     <xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>  
  
     <xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>  
  
    > [!NOTE]
    >  `IOleInPlaceComponent` Интерфейс используется для предотвращения слияние меню OLE 2.  
  
     Ваш `IOleCommandTarget` реализация обрабатывает команды, такие как **Вырезать**, **копирования**, и **вставить**. При реализации `IOleCommandTarget`, решить, требуется ли редактора свой собственный vsct-файл для определения структуры меню свои собственные команды или если он может реализовывать стандартных команд, определенных в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Как правило редакторы использовать и расширять меню IDE и определить свои собственные панели инструментов. Тем не менее часто бывает редактора для определения собственных конкретных команд, помимо использования набора стандартных команд интегрированной среды разработки. Для этого редактора необходимо объявить стандартные команды, он использует, а затем определите новые команды, контекстные меню, меню верхнего уровня и панелей инструментов в vsct-файл. При создании активации на месте редактора, затем реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> и определить меню и панелей инструментов для редактора в vsct-файл вместо использования слияние меню OLE 2.  
  
-   Чтобы команды меню, которые частенько получает сильнейший в пользовательском Интерфейсе, следует использовать существующие команды в интегрированной среде разработки до изобретать новые команды. Общие команды определяются в SharedCmdDef.vsct и ShellCmdDef.vsct. Эти файлы устанавливаются по умолчанию в подкаталоге VisualStudioIntegration\Common\Inc вашей [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] установки.  
  
-   `ISelectionContainer` можно выразить один или несколько выбранных элементов. Каждого выбранного объекта реализован в виде `IDispatch` объекта.  
  
-   IDE реализует `IOleUndoManager` как служба, доступная из <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> или объектом, который может быть создан через <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>. Пользовательский редактор реализует `IOleUndoUnit` интерфейс для каждого `Undo` действие.  
  
-   В двух местах пользовательского редактора может предоставлять объекты автоматизации:  
  
    -   `Document.Object`  
  
    -   `Window.Object`  
  
## <a name="see-also"></a>См. также  
 [Дополнение к модели автоматизации](../extensibility/internals/contributing-to-the-automation-model.md)   
 [Практическое руководство. Предоставление контекста для редакторов](../extensibility/how-to-provide-context-for-editors.md)

