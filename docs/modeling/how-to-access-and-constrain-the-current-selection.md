---
title: Практическое руководство. Предоставление и ограничение доступа к текущему выделению
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, accessing the current selection
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d8d10efbe87177f9caa6e3471e548569a59c3e47
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667216"
---
# <a name="how-to-access-and-constrain-the-current-selection"></a>Практическое руководство. Предоставление и ограничение доступа к текущему выделению

При написании команды или обработчика жестов для конкретного доменного языка можно определить, какой элемент пользователь щелкнул правой кнопкой мыши. Можно также запретить выбор некоторых фигур или полей. Например, можно задать, что при нажатии пользователем декоратора значка выбирается фигура, содержащая этот элемент. Ограничение выбора таким способом сокращает количество обработчиков, которые необходимо написать. Это также упрощает для пользователя, который может щелкнуть в любом месте фигуры, не избегая декоратора.

## <a name="access-the-current-selection-from-a-command-handler"></a>Доступ к текущему выделению из обработчика команд

Класс набора команд для доменного языка содержит обработчики команд для пользовательских команд. Класс <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>, от которого наследуется класс набора команд для доменного языка, предоставляет несколько элементов для доступа к текущему выделению.

В зависимости от команды обработчик команд может потребовать выбора в конструкторе моделей, в обозревателе моделей или в активном окне.

### <a name="to-access-selection-information"></a>Доступ к сведениям о выборе

1. Класс <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> определяет следующие члены, которые можно использовать для доступа к текущему выделению.

    |Член|Описание|
    |-|-|
    |Метод <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsAnyDocumentSelectionCompartment%2A>|Возвращает `true`, если какой-либо из элементов, выбранных в конструкторе моделей, является фигурой секции; в противном случае `false`.|
    |Метод <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsDiagramSelected%2A>|Возвращает `true`, если схема выбрана в конструкторе моделей. в противном случае `false`.|
    |Метод <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleDocumentSelection%2A>|Возвращает `true`, если в конструкторе моделей выбран ровно один элемент; в противном случае `false`.|
    |Метод <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleSelection%2A>|Возвращает `true`, если в активном окне выбран ровно один элемент; в противном случае `false`.|
    |Свойство<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentDocumentSelection%2A>|Возвращает доступную только для чтения коллекцию элементов, выбранных в конструкторе моделей.|
    |Свойство<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentSelection%2A>|Возвращает доступную только для чтения коллекцию элементов, выбранных в активном окне.|
    |Свойство<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleDocumentSelection%2A>|Возвращает первичный элемент выбранного элемента в конструкторе моделей.|
    |Свойство<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleSelection%2A>|Возвращает первичный элемент выделенного фрагмента в активном окне.|

2. Свойство <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet.CurrentDocView%2A> класса <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> предоставляет доступ к объекту <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView>, который представляет окно конструктора моделей и предоставляет дополнительный доступ к выбранным элементам в конструкторе моделей.

3. Кроме того, созданный код определяет свойство окна инструментов обозревателя и свойство выбора обозревателя в классе набора команд для предметно-ориентированного языка.

    - Свойство окна инструментов обозревателя возвращает экземпляр класса окна инструментов обозревателя для предметно-ориентированного языка. Класс окна инструментов обозревателя является производным от класса <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow> и представляет обозреватель моделей для предметно-ориентированного языка.

    - Свойство `ExplorerSelection` Возвращает выбранный элемент в окне обозревателя моделей для предметно-ориентированного языка.

## <a name="determine-which-window-is-active"></a>Определение активного окна

Интерфейс <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> содержит определяет члены, которые предоставляют доступ к текущему состоянию выбора в оболочке. Объект <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> можно получить из класса Package или класса набора команд для доменного языка с помощью свойства `MonitorSelection`, определенного в базовом классе каждого из них. Класс Package является производным от класса <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage>, а класс набора команд является производным от класса <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>.

### <a name="to-determine-from-a-command-handler-what-type-of-window-is-active"></a>Определение типа активного окна с помощью обработчика команд

1. Свойство <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.MonitorSelection%2A> класса <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> возвращает объект <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>, который предоставляет доступ к текущему состоянию выделения в оболочке.

2. Свойство <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService.CurrentSelectionContainer%2A> интерфейса <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> получает активный контейнер выбора, который может отличаться от активного окна.

3. Добавьте следующие свойства в класс набора команд для конкретного доменного языка, чтобы определить, какой тип окна является активным.

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

## <a name="constrain-the-selection"></a>Ограничить выбор

Добавляя правила выбора, можно управлять выбором элементов при выборе пользователем элемента модели. Например, чтобы разрешить пользователю обрабатывать несколько элементов как единое целое, можно использовать правило выбора.

### <a name="to-create-a-selection-rule"></a>Создание правила выбора

1. Создание файла пользовательского кода в проекте DSL

2. Определите класс правил выбора, производный от класса <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules>.

3. Переопределите метод <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules.GetCompliantSelection%2A> класса правила выбора, чтобы применить критерии выбора.

4. Добавьте определение разделяемого класса для класса ClassDiagram в файл пользовательского кода.

     Класс `ClassDiagram` является производным от класса <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram> и определяется в созданном файле кода Diagram.cs в проекте DSL.

5. Переопределите свойство <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> класса `ClassDiagram`, чтобы получить настраиваемое правило выбора.

     Реализация свойства <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> по умолчанию получает объект правила выбора, который не изменяет выделенный фрагмент.

### <a name="example"></a>Пример

В следующем файле кода создается правило выбора, которое расширяет выделенный фрагмент, добавляя все экземпляры каждой из первоначально выбранных фигур домена.

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