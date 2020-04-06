---
title: 'Пошаговая прогулка: Добавление функций в пользовательский редактор Документы Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - add features
ms.assetid: bfe083b6-3e35-4b9c-ad4f-b30b9ff412a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b145dd4d82887122009553afd883abb6cade849e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697789"
---
# <a name="walkthrough-add-features-to-a-custom-editor"></a>Прохождение: Добавление функций в пользовательский редактор
После создания пользовательского редактора можно добавить в него больше функций.

## <a name="to-create-an-editor-for-a-vspackage"></a>Создание редактора для VSPackage

1. Создайте пользовательский редактор с помощью шаблона проекта Visual Studio Package.

     Для получения дополнительной информации [см.](../extensibility/walkthrough-creating-a-custom-editor.md)

2. Решите, хотите ли редактор поддерживать одно представление или несколько представлений.

     Редактору, который поддерживает команду **New Window** или имеет представление формы и представление кода, требуются отдельные объекты данных документов и объекты представления документов. В редакторе, который поддерживает только одно представление, объект данных документа и объект представления документа могут быть реализованы на одном объекте.

     Для примера нескольких представлений [см.](../extensibility/supporting-multiple-document-views.md)

3. Реализация фабрики редакторов <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> путем настройки интерфейса.

     Для получения дополнительной [информации см.](../extensibility/editor-factories.md)

4. Решите, хотите ли редактор использовать активацию на месте или упрощенное встраивание для управления окном объекта представления документа.

     Упрощенное окно редактора встраивания размещает стандартное представление документа, в то время как окно редактора активации на месте размещает элемент управления ActiveX или другой активный объект в качестве представления документа. Для получения дополнительной информации [In-place activation](/visualstudio/misc/in-place-activation?view=vs-2015)см. [Simplified Embedding](../extensibility/simplified-embedding.md)

5. Реализация <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейса для обработки команд.

6. Обеспечить сохранение документов и ответ на внешние изменения файлов:

    1. Чтобы сохранить файл, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> реализовать и на объекте данных документа редактора.

    2. Чтобы реагировать на внешние <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> изменения файлов, реализуйте и на объекте данных документа редактора.

        > [!NOTE]
        > Позвоните, `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx> чтобы получить `IVsFileChangeEx`указатель на .

7. Координировать работу событий по проверке исходного кода с помощью управления исходным кодом. Выполните следующие действия.

    1. Получить указатель, `IVsQueryEditQuerySave2` позвонив `QueryService` на <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>.

    2. При первом событии отсеивайте, позвоните в <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> метод.

         Этот метод побуждает пользователя проверить файл, если он еще не выбыл. Убедитесь в том, чтобы обрабатывать "файл не проверил" условие, чтобы предотвратить ошибки.

    3. Аналогичным образом, прежде чем <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> сохранить файл, позвоните в метод.

         Этот метод предлагает пользователю сохранить файл, если он не был сохранен или если он изменился после последнего сохранения.

8. Включите окно **Свойств** для отображения свойств для текста, выбранного в редакторе. Выполните следующие действия.

    1. Звоните <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> каждый раз, когда изменение <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>выбора текста, проходя в вашей реализации .

    2. `QueryService` Позвоните <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> на службу, <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>чтобы получить указатель на .

9. Позволяет пользователям перетаскивать и сбрасывать элементы между редактором и **Toolbox**или между внешними редакторами (например, Microsoft Word) и **Toolbox.** Выполните следующие действия.

    1. Внедрить `IDropTarget` на редакторе, чтобы предупредить IDE, что ваш редактор является целевой броской.

    2. Реализация <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> интерфейса на представлении, чтобы редактор мог включить и отключить элементы в **Toolbox.**

    3. Реализация <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A> и `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox> вызов службы для получения <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> указателя на интерфейсы и интерфейсы.

         Эти шаги позволяют VSPackage добавлять новые элементы в **Toolbox.**

10. Решите, нужны ли вам другие дополнительные функции для редактора.

    - Если вы хотите, чтобы редактор поддерживал поиск <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>и замену команд, реализуйте.

    - Если в редакторе требуется использовать окно инструмента `IVsDocOutlineProvider`набросков документов, реализуйте.

    - Если вы хотите использовать панель статуса <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> в `QueryService` редакторе, реализуйте и вызывайте, <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> чтобы получить указатель `IVsStatusBar`на .

         Например, редактор может отображать информацию о строке/ колонке, режиме выбора (поток/поле) и режиме вставки (вставить/ переутомить).

    - Если вы хотите, чтобы `Undo` редактор поддерживал команду, рекомендуемый метод заключается в использовании модели диспетчера OLE undo. В качестве альтернативы можно понавести `Undo` редактора напрямую.

11. Создавайте информацию о реестре, включая GUID для VSPackage, меню, редактор и другие функции.

     Ниже приводится общий пример кода, который вы бы положить в свой сценарий *файла .rgs,* чтобы продемонстрировать, как правильно зарегистрировать редактор.

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

12. Реализация чувствительной к контексту поддержки справки.

     Этот шаг позволяет предоставить f1 Справка и динамическая справка окно поддержки элементов в вашем редакторе. Для получения дополнительной [How to: Provide context for editors](/visualstudio/extensibility/how-to-provide-context-for-editors?view=vs-2015)информации см.

13. Вынаните модель объекта автоматизации `IDispatch` от редактора, реализовав интерфейс.

     Для получения дополнительной информации см. [Contributing to the Automation Model](../extensibility/internals/contributing-to-the-automation-model.md).

## <a name="robust-programming"></a>Отказоустойчивость

- Экземпляр редактора создается, когда <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> IDE вызывает метод. Если редактор поддерживает несколько представлений, `CreateEditorInstance` создается как данные документа, так и объекты представления документа. Если объект данных документа уже открыт, `punkDocDataExisting` ненулл-значение передается `IVsEditorFactory::CreateEditorInstance`. Реализация фабрики редактора должна определить, совместим ли существующий объект данных документа, задав запрос на соответствующие интерфейсы. Для получения дополнительной [информации](../extensibility/supporting-multiple-document-views.md)см.

- Если вы используете упрощенный подход к <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> встраиванию, реализуй интерфейс.

- Если вы решили использовать активацию на месте, реализуем следующие интерфейсы:

   <xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>

   <xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>

   <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>

  > [!NOTE]
  > Интерфейс `IOleInPlaceComponent` используется, чтобы избежать слияния меню OLE 2.

   Реализация `IOleCommandTarget` обрабатывает такие команды, как **Cut,** **Copy**и **Paste.** При реализации, `IOleCommandTarget`решить, требуется ли редактору свой собственный файл *.vsct* для определения [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]своей собственной структуры меню команд или если он может реализовать стандартные команды, определенные . Как правило, редакторы используют и расширяют меню IDE и определяют свои собственные панели инструментов. Однако редактору часто необходимо определить свои собственные конкретные команды в дополнение к использованию стандартного набора команд IDE. Редактор должен декларировать стандартные команды, которые он использует, а затем определять любые новые команды, контекстные меню, меню верхнего уровня и панели инструментов в файле *.vsct.* Если вы создаете редактор активации <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> на месте, реализуйте и определяйте меню и панели инструментов для редактора в файле *.vsct* вместо того, чтобы использовать слияние меню OLE 2.

- Чтобы предотвратить скученность команды меню в uI, следует использовать существующие команды в IDE, прежде чем изобретать новые команды. Общие команды определяются в *SharedCmdDef.vsct* и *ShellCmdDef.vsct.* Эти файлы устанавливаются по умолчанию в субдиректоре [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] установки VisualStudioIntegration-Common-Inc.

- `ISelectionContainer`может выражать как одиночный, так и несколько вариантов. Каждый выбранный объект `IDispatch` реализуется как объект.

- IDE реализует `IOleUndoManager` как услугу, <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> доступную от объекта или как объект, который может быть мгновенно через <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>. Ваш редактор реализует `IOleUndoUnit` интерфейс `Undo` для каждого действия.

- Существует два места, где пользовательский редактор может предоставить объекты автоматизации:

  - `Document.Object`

  - `Window.Object`

## <a name="see-also"></a>См. также

- [Внести свой вклад в модель автоматизации](../extensibility/internals/contributing-to-the-automation-model.md)
