---
title: 'Пошаговое руководство: Добавление функций в специализированный редактор | Документация Майкрософт'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - add features
ms.assetid: bfe083b6-3e35-4b9c-ad4f-b30b9ff412a5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7062f44fe119858e579a53325deca0ea04b46475
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49873023"
---
# <a name="walkthrough-add-features-to-a-custom-editor"></a>Пошаговое руководство: Добавление компонентов к пользовательского редактора
После создания настраиваемого редактора, можно добавить дополнительные функции к нему.  
  
## <a name="to-create-an-editor-for-a-vspackage"></a>Чтобы создать редактор для VSPackage  
  
1.  Создание пользовательского редактора, используя шаблон проекта пакета Visual Studio.  
  
     Дополнительные сведения см. в разделе [Пошаговое руководство: Создание пользовательского редактора](../extensibility/walkthrough-creating-a-custom-editor.md).  
  
2.  Решите, следует ли редактора для поддержки единое представление или несколько представлений.  
  
     В редакторе, поддерживающем **новое окно** команды или имеет представление формы и представление кода, требует отдельного документа объекты и объекты представления документа. В редакторе, который поддерживает только одно представление объект данных документа и объект представления документа может осуществляться на этом же объекте.  
  
     Пример того, несколько представлений, см. в разделе [поддерживать несколько представлений документа](../extensibility/supporting-multiple-document-views.md).  
  
3.  Реализуйте фабрику редактора, настроив <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> интерфейс.  
  
     Дополнительные сведения см. в разделе [фабрики редакторов](../extensibility/editor-factories.md).  
  
4.  Определите, ли ваш редактор для использования встроенной активации, или упрощенное внедрение для управления окна объекта представления документа.  
  
     Упрощенное внедрение окно редактора размещает представления стандартного документа, а окно редактора встроенной активации размещает элемент управления ActiveX или другого активного объекта, как ее представление документа. Дополнительные сведения см. в разделе [упрощенное внедрение](../extensibility/simplified-embedding.md) и [встроенная активация](../extensibility/in-place-activation.md).  
  
5.  Реализуйте <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейса для обработки команд.  
  
6.  Укажите сохраняемость документа и ответ на изменения внешнего файла.  
  
    1.  Чтобы сохранить файл, реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> и <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> на объект данных документа в редакторе.  
  
    2.  Чтобы реагировать на изменения внешнего файла, реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> на объект данных документа в редакторе.  
  
        > [!NOTE]
        >  Вызовите `QueryService` на <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx> для получения указателя на `IVsFileChangeEx`.  
  
7.  Координируйте события редактирования документов с контролем исходного кода. Выполните следующие действия.  
  
    1.  Получить указатель на `IVsQueryEditQuerySave2` путем вызова `QueryService` на <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>.  
  
    2.  Когда происходит первое событие редактирования, вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> метод.  
  
         Этот метод предлагает пользователю извлечь файл, если он еще не извлечен. Убедитесь, что условие «файл не извлечен», чтобы избежать ошибок обработки.  
  
    3.  Аналогичным образом, прежде чем сохранить файл, вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> метод.  
  
         Этот метод предлагает пользователю сохранить файл, если он еще не был сохранен, или если он изменен с момента последнего сохранения.  
  
8.  Включить **свойства** окно для отображения свойств для текста, выделенного в редакторе. Выполните следующие действия.  
  
    1.  Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> выделение текста каждый раз изменяется, передав в реализации <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>.  
  
    2.  Вызовите `QueryService` на <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> службу для получения указателя на <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>.  
  
9. Разрешить пользователям перетаскивать элементы между редактором и **элементов**, или между внешних редакторов (например, Microsoft Word) и **элементов**. Выполните следующие действия.  
  
    1.  Реализуйте `IDropTarget` на редактора для создания предупреждения интегрированной среды разработки, что редактора является целью перетаскивания.  
  
    2.  Реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> интерфейс для представления, поэтому редактора можно включать и отключать элементы в **элементов**.  
  
    3.  Реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A> и вызвать `QueryService` на <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox> службу для получения указателя на <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> интерфейсов.  
  
         Эти шаги позволяют включить VSPackage для добавления новых элементов к **элементов**.  
  
10. Решите, следует ли другие дополнительные возможности для редактора.  
  
    -   Если вы хотите, чтобы редактора для поддержки найти и заменить команды, реализовать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>.  
  
    -   Если вы хотите использовать окно инструментов структуры документа в редакторе, реализовать `IVsDocOutlineProvider`.  
  
    -   Если вы хотите использовать строку состояния в редакторе, реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> и вызвать `QueryService` для <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> для получения указателя на `IVsStatusBar`.  
  
         Например, редактор можно отобразить строки и сведения о столбцах, режим выбора (потоковая передача / поле) и режим вставки (insert / overstrike).  
  
    -   Если вы хотите, чтобы редактора для поддержки `Undo` команды, рекомендуется использовать модель диспетчера отмены OLE. Кроме того, что дескриптор редактор `Undo` команду напрямую.  
  
11. Создание реестра сведения, включая идентификаторы GUID для пакета VSPackage, меню, редактора и другие функции.  
  
     Ниже приведен общий пример кода, который можно поместить в вашей *.rgs* файл скрипта, чтобы продемонстрировать, как по правильной регистрации редактора.  
  
    ```csharp  
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
  
     Этот шаг позволяет обеспечить поддержку справки F1 и динамической справки окна, для элементов в редакторе. Дополнительные сведения см. в разделе [как: предоставить контекст для редакторов](../extensibility/how-to-provide-context-for-editors.md).  
  
13. Предоставляют объектную модель автоматизации из редактора, реализовав `IDispatch` интерфейс.  
  
     Для получения дополнительной информации см. [Contributing to the Automation Model](../extensibility/internals/contributing-to-the-automation-model.md).  
  
## <a name="robust-programming"></a>Отказоустойчивость  
  
- Экземпляр редактора создается в том случае, когда вызывает интегрированной среды разработки <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> метод. Если редактор поддерживает несколько представлений, `CreateEditorInstance` создает данные документа и объекты представления документа. Если объект данных документа уже открыть, отличный от null `punkDocDataExisting` значение передается `IVsEditorFactory::CreateEditorInstance`. Реализации фабрики редактора необходимо определить, совместима ли существующий объект данных документа, запрашивая соответствующие интерфейсы на нем. Дополнительные сведения см. в разделе [Supporting Multiple Document Views](../extensibility/supporting-multiple-document-views.md).  
  
- Если вы используете упрощенный способ внедрения, реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> интерфейс.  
  
- Если вы решили использовать активацию на месте, реализуйте следующие интерфейсы:  
  
   <xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>  
  
   <xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>  
  
   <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>  
  
  > [!NOTE]
  >  `IOleInPlaceComponent` Интерфейс используется для предотвращения слияние меню OLE 2.  
  
   Ваш `IOleCommandTarget` реализация обрабатывает команды, такие как **Вырезать**, **копирования**, и **вставить**. При реализации `IOleCommandTarget`, решить, является ли ваш редактор должен иметь собственную *.vsct* файл, чтобы определить свой собственный структура команды меню или если он может реализовывать стандартных команд, определенных в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Как правило редакторы использовать и расширять меню IDE и определить свои собственные панели инструментов. Тем не менее часто бывает редактора для определения собственных конкретных команд, помимо использования набора стандартных команд интегрированной среды разработки. Редактора необходимо объявить стандартные команды, он использует и затем определить новые команды, контекстные меню, меню верхнего уровня и панелей инструментов в *.vsct* файла. При создании активации на месте редактора, реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> и определить для редактора в меню и панелей инструментов *.vsct* файл, а не с помощью OLE 2 слияние меню.  
  
- Чтобы команды меню, которые частенько получает сильнейший в пользовательском Интерфейсе, следует использовать существующие команды в интегрированной среде разработки до изобретать новые команды. Общие команды определены в *SharedCmdDef.vsct* и *ShellCmdDef.vsct*. Эти файлы устанавливаются по умолчанию в подкаталоге VisualStudioIntegration\Common\Inc вашей [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] установки.  
  
- `ISelectionContainer` можно выразить один или несколько выбранных элементов. Каждого выбранного объекта реализован в виде `IDispatch` объекта.  
  
- IDE реализует `IOleUndoManager` как служба, доступная из <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> или объектом, который может быть создан через <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>. Пользовательский редактор реализует `IOleUndoUnit` интерфейс для каждого `Undo` действие.  
  
- В двух местах пользовательского редактора может предоставлять объекты автоматизации:  
  
  -   `Document.Object`  
  
  -   `Window.Object`  
  
## <a name="see-also"></a>См. также  
 [Участие в модели автоматизации](../extensibility/internals/contributing-to-the-automation-model.md)   
 [Практическое: предоставить контекст для редакторов](../extensibility/how-to-provide-context-for-editors.md)