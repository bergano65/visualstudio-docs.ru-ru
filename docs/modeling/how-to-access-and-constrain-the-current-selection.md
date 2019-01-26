---
title: Как выполнить Предоставление и ограничение доступа к текущему выделению
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, accessing the current selection
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: bb87e8785d58354b837896e4a5af580d348e61f2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54954168"
---
# <a name="how-to-access-and-constrain-the-current-selection"></a>Как выполнить Предоставление и ограничение доступа к текущему выделению

При написании обработчика команды или жеста для вашего доменного языка, можно определить, какой элемент пользователь щелкнул правой кнопкой мыши. Можно также предотвратить некоторые формы или поля выбора. Например можно упорядочить, что когда пользователь щелкает значок декоратор, фигура, содержащая его вместо него будет выбран. Ограничение выбора таким образом уменьшает количество обработчиков, которые необходимо написать. Он также упрощает для пользователей, потому что можно щелкните в любом месте фигуры без необходимости избежать декоратора.

## <a name="access-the-current-selection-from-a-command-handler"></a>Доступ к текущее выделение из обработчика команд

Класс набора команд для доменного языка содержит обработчики команд для ваши пользовательские команды. <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> Класс, от которого наследует класс набора команд для доменного языка, предоставляет несколько членов для доступа к текущего выделения.

В зависимости от команды обработчик команд может потребоваться выделения в конструкторе моделей, обозреватель моделей или активного окна.

### <a name="to-access-selection-information"></a>Для доступа к информации выбора

1.  <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> Класс определяет следующие члены, которые могут использоваться для доступа к текущего выделения.

    |Член|Описание:|
    |-|-|
    |Метод <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsAnyDocumentSelectionCompartment%2A>|Возвращает `true` при выполнении любого из элементов, выбранных в конструкторе моделей фигурой секции; в противном случае `false`.|
    |Метод <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsDiagramSelected%2A>|Возвращает `true` Если диаграммы, выбранных в конструкторе моделей, в противном случае — `false`.|
    |Метод <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleDocumentSelection%2A>|Возвращает `true` если ровно один элемент, выбранный в конструкторе моделей, в противном случае — `false`.|
    |Метод <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleSelection%2A>|Возвращает `true` если ровно один элемент, выбранный в активном окне; в противном случае `false`.|
    |Свойство <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentDocumentSelection%2A>|Возвращает доступную только для чтения коллекцию элементов, выбранных в конструкторе моделей.|
    |Свойство <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentSelection%2A>|Возвращает доступную только для чтения коллекцию элементов, выбранных в активном окне.|
    |Свойство <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleDocumentSelection%2A>|Получает основной элемент выделения в конструкторе моделей.|
    |Свойство <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleSelection%2A>|Получает основной элемент выделения в активном окне.|

2.  <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet.CurrentDocView%2A> Свойство <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> класс предоставляет доступ к <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView> объект, представляющий окно конструктора моделей и предоставляет дополнительный доступ выбранных элементов в конструкторе моделей.

3.  Кроме того созданный код определяет свойство средство окно проводника и выбора Вот свойство проводника в команде задайте класс для доменного языка.

    -   Свойство окна инструментов обозревателя возвращает экземпляр класса окна инструментов обозревателя для доменного языка. Класс окна инструментов обозревателя является производным от <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow> класса и представляет обозреватель модели для доменного языка.

    -   `ExplorerSelection` Свойство возвращает выбранного элемента в окне обозревателя моделей для доменного языка.

## <a name="determine-which-window-is-active"></a>Определить, какое окно является активным

<xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> Содержит интерфейс определяет члены, которые предоставляют доступ к текущему состоянию выделения в оболочке. Вы можете получить <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> классу пакета или классе наборов команд для доменного языка через объект `MonitorSelection` свойства, определенные в базовом классе каждого из них. Класс пакета является производным от <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage> класс и класс набора команд является производным от <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> класса.

### <a name="to-determine-from-a-command-handler-what-type-of-window-is-active"></a>Чтобы определить обработчик команд активен какой тип окна

1.  <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.MonitorSelection%2A> Свойство <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> возвращает <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> объект, предоставляющий доступ к текущему состоянию выделения в оболочке.

2.  <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService.CurrentSelectionContainer%2A> Свойство <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> интерфейс получает активный контейнер выделения, которое может отличаться от активного окна.

3.  Добавьте следующие свойства в команду набора классов для вас доменный язык, чтобы определить, какой тип окна активен.

    ```csharp
    // using Microsoft.VisualStudio.Modeling.Shell;

    // Returns true if the model designer is the active selection container;
    // otherwise, false.
    protected bool IsDesignerActive
    {
        get
        {
            return (this.MonitorSelection.CurrentSelectionContainer
                is DiagramDocView);
        }
    }

    // Returns true if the model explorer is the active selection container;
    // otherwise, false.
    protected bool IsExplorerActive
    {
        get
        {
            return (this.MonitorSelection.CurrentSelectionContainer
                is ModelExplorerToolWindow);
        }
    }
    ```

## <a name="constrain-the-selection"></a>Ограничения выбора

Добавление правила выбора, вы можете управлять, какие элементы выбраны в том случае, когда пользователь выбирает элемент в модели. Например чтобы разрешить пользователю обрабатывать несколько элементов как единое целое, можно использовать правило выбора.

### <a name="to-create-a-selection-rule"></a>Чтобы создать правило выбора

1.  Создайте файл пользовательского кода в проекте DSL

2.  Определите класс правила выбора, который является производным от <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules> класса.

3.  Переопределить <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules.GetCompliantSelection%2A> метод класса правил выбора для применения условия выбора.

4.  Добавьте определение разделяемого класса для класса ClassDiagram в файл пользовательского кода.

     `ClassDiagram` Класс является производным от <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram> класса и определен в файле сформированного кода Diagram.cs, в проекте DSL.

5.  Переопределить <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> свойство `ClassDiagram` класса для возвращения правило пользовательского выбора.

     Реализация по умолчанию <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> свойство возвращает объект правила выделения, не изменяет выделение.

### <a name="example"></a>Пример

Следующий файл кода создает правило выбора, который расширяет выделение для включения всех экземпляров для каждой фигуры домена, которые изначально был выбран.

```csharp
using System;
using System.Collections.Generic;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;

namespace CompanyName.ProductName.GroupingDsl
{
    public class CustomSelectionRules : DiagramSelectionRules
    {
        protected Diagram diagram;
        protected IElementDirectory elementDirectory;

        public CustomSelectionRules(Diagram diagram)
        {
            if (diagram == null) throw new ArgumentNullException();

            this.diagram = diagram;
            this.elementDirectory = diagram.Store.ElementDirectory;
        }

        /// <summary>Called by the design surface to allow selection filtering.
        /// </summary>
        /// <param name="currentSelection">[in] The current selection before any
        /// ShapeElements are added or removed.</param>
        /// <param name="proposedItemsToAdd">[in/out] The proposed DiagramItems to
        /// be added to the selection.</param>
        /// <param name="proposedItemsToRemove">[in/out] The proposed DiagramItems
        /// to be removed from the selection.</param>
        /// <param name="primaryItem">[in/out] The proposed DiagramItem to become
        /// the primary DiagramItem of the selection. A null value signifies that
        /// the last DiagramItem in the resultant selection should be assumed as
        /// the primary DiagramItem.</param>
        /// <returns>true if some or all of the selection was accepted; false if
        /// the entire selection proposal was rejected. If false, appropriate
        /// feedback will be given to the user to indicate that the selection was
        /// rejected.</returns>
        public override bool GetCompliantSelection(
            SelectedShapesCollection currentSelection,
            DiagramItemCollection proposedItemsToAdd,
            DiagramItemCollection proposedItemsToRemove,
            DiagramItem primaryItem)
        {
            if (currentSelection.Count == 0 && proposedItemsToAdd.Count == 0) return true;

            HashSet<DomainClassInfo> itemsToAdd = new HashSet<DomainClassInfo>();

            foreach (DiagramItem item in proposedItemsToAdd)
            {
                if (item.Shape != null)
                    itemsToAdd.Add(item.Shape.GetDomainClass());
            }
            proposedItemsToAdd.Clear();
            foreach (DomainClassInfo classInfo in itemsToAdd)
            {
                foreach (ModelElement element
                    in this.elementDirectory.FindElements(classInfo, false))
                {
                    if (element is ShapeElement)
                    {
                        proposedItemsToAdd.Add(
                            new DiagramItem((ShapeElement)element));
                    }
                }
            }

            return true;
        }
    }

    public partial class ClassDiagram
    {
        protected CustomSelectionRules customSelectionRules = null;

        protected bool multipleSelectionMode = true;

        public override DiagramSelectionRules SelectionRules
        {
            get
            {
                if (multipleSelectionMode)
                {
                    if (customSelectionRules == null)
                    {
                        customSelectionRules = new CustomSelectionRules(this);
                    }
                    return customSelectionRules;
                }
                else
                {
                    return base.SelectionRules;
                }
            }
        }
    }
}
```

## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>
- <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage>
- <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView>
- <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow>
- <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>
- <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules>
- <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>