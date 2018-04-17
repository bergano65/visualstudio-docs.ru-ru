---
title: 'Как: доступ, а также ограничить текущее выделение | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, accessing the current selection
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 278947fdb9851bdc54a80ea7f2d47d72deba300e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-access-and-constrain-the-current-selection"></a>Практическое руководство. Предоставление и ограничение доступа к текущему выделению
При написании обработчика команды или жеста для вашего доменного языка, можно определить, какой элемент, который пользователь щелкнул правой кнопкой мыши. Вы также можете запретить от выбранной фигуры и поля. Например можно расположить в том, что когда пользователь щелкает значок decorator, фигуру, которая содержит его вместо него будет выбран. Ограничить выбор таким образом уменьшает количество обработчиков, которые необходимо написать. Он также упрощает для пользователей, потому что можно щелкните в любом месте фигуры без необходимости избежать декоратор.  
  
## <a name="accessing-the-current-selection-from-a-command-handler"></a>Доступ к выделенной из обработчика команд  
 Команда set-класс для доменного языка содержит обработчики команд для пользовательские команды. <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> Класс, от которого наследует класс набор команд для доменного языка, предоставляет несколько членов для доступа к текущей выделенной области.  
  
 В зависимости от команды обработчик команд может потребоваться выбор в конструкторе моделей, обозреватель модели или активного окна.  
  
#### <a name="to-access-selection-information"></a>Для доступа к сведениям выделения  
  
1.  <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> Класс определяет следующие члены, которые могут использоваться для доступа к текущей выделенной области.  
  
    |Член|Описание|  
    |------------|-----------------|  
    |Метод <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsAnyDocumentSelectionCompartment%2A>|Возвращает `true` при выполнении любого из элементов, выбранных в конструкторе моделей фигура секции; в противном случае `false`.|  
    |Метод <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsDiagramSelected%2A>|Возвращает `true` Если диаграммы, выбранных в конструкторе моделей, в противном случае — `false`.|  
    |Метод <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleDocumentSelection%2A>|Возвращает `true` если ровно один элемент, выбранный в конструкторе моделей, в противном случае — `false`.|  
    |Метод <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleSelection%2A>|Возвращает `true` если ровно один элемент выбран в активном окне; в противном случае — `false`.|  
    |Свойство <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentDocumentSelection%2A>|Возвращает доступную только для чтения коллекцию элементов, выбранных в конструкторе моделей.|  
    |Свойство <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentSelection%2A>|Возвращает коллекцию элементов, выбранных в активном окне только для чтения.|  
    |Свойство <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleDocumentSelection%2A>|Возвращает основной элемент выделения в конструкторе моделей.|  
    |Свойство <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleSelection%2A>|Возвращает основной элемент выделения в активном окне.|  
  
2.  <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet.CurrentDocView%2A> Свойство <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> класс предоставляет доступ к <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView> объект, представляющий окно конструктора моделей и предоставляет дополнительные права доступа выбранных элементов в конструкторе моделей.  
  
3.  Кроме того созданный код определяет свойство окна инструментов проводника и свойство выбора проводника в команде задать класс для доменного языка.  
  
    -   Свойство окна инструмента обозревателя возвращает экземпляр класса окна обозревателя средство для доменного языка. Класс окна инструментов обозревателя является производным от <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow> класса и представляет Обозреватель моделей для доменного языка.  
  
    -   `ExplorerSelection` Свойство возвращает элемент, выбранный в окне обозревателя моделей для доменного языка.  
  
## <a name="determining-which-window-is-active"></a>Определение того, какое окно является активным  
 <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> Содержит интерфейс определяет члены, предоставляющие доступ к состоянию текущего выделения в оболочке. Вы можете получить <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> пакета класс или класс набор команд для доменного языка через объект `MonitorSelection` свойства, определенные в базовом классе каждого. Класс пакета является производным от <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage> класс и команда set-класс является производным от <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> класса.  
  
#### <a name="to-determine-from-a-command-handler-what-type-of-window-is-active"></a>Чтобы определить, является допустимым обработчиком команд активен тип окна  
  
1.  <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.MonitorSelection%2A> Свойство <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> возвращает <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> объект, предоставляющий доступ к состоянию текущего выделения в оболочке.  
  
2.  <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService.CurrentSelectionContainer%2A> Свойство <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> интерфейс возвращает контейнер активное выделение, который может отличаться от активного окна.  
  
3.  Добавьте следующие свойства для команды set-класс для вас доменный язык, чтобы определить, какой тип окна активен.  
  
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
  
## <a name="constraining-the-selection"></a>Ограничить выбор  
 Добавляя правила выбора, можно выбрать, какие элементы выбраны в том случае, когда пользователь выбирает элемент в модели. Например чтобы разрешить пользователю обрабатывать как единое целое число элементов, можно использовать правила выбора.  
  
#### <a name="to-create-a-selection-rule"></a>Чтобы создать правило выбора  
  
1.  Создайте файл пользовательского кода в проекте DSL  
  
2.  Определение класса правила выбора, который является производным от <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules> класса.  
  
3.  Переопределить <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules.GetCompliantSelection%2A> метод класса выбора правил для применения условия выбора.  
  
4.  Добавьте определение разделяемого класса для класса ClassDiagram файл пользовательского кода.  
  
     `ClassDiagram` Класс является производным от <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram> класса и определяется в файле сформированного кода Diagram.cs, в проекте DSL.  
  
5.  Переопределить <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> свойство `ClassDiagram` класса для возвращения выбора настраиваемого правила.  
  
     Реализация по умолчанию <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> свойство возвращает объект правила выделения, нельзя изменить выбор.  
  
### <a name="example"></a>Пример  
 В следующем файле кода создает правило выбора, которая расширяется выделения, чтобы включить все экземпляры каждого домена формы, которые изначально был установлен.  
  
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
 <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>   
 <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage>   
 <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView>   
 <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow>   
 <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>   
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules>   
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>