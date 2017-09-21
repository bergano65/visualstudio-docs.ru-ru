---
title: "Практическое руководство. Предоставление и ограничение доступа к текущему выделению | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Доменный язык, доступ к текущему выделению"
ms.assetid: 2990981e-dfae-416f-b0d0-7197f1242dfa
caps.latest.revision: 14
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 14
---
# Практическое руководство. Предоставление и ограничение доступа к текущему выделению
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

При написании команды или обработчика жестов для вашего доменного языка, можно определить, какой элемент пользователь щелкнул правой кнопкой мыши. Можно также предотвратить некоторые формы или поля выбора. Например можно упорядочить, когда пользователь щелкает значок декоратор, фигуры, содержащей его вместо него будет выбран. Ограничение выбора таким образом уменьшает количество обработчиков, которые нужно будет написать. Он также облегчает для пользователя, который может щелкните в любом месте фигуры без необходимости избежать декоратора.  
  
## Доступ к выделенной из обработчика команды  
 Класс набора команд для доменного языка содержит обработчики команд для пользовательских команд.<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> Класс, от которого наследует класс набора команд для доменного языка, предоставляет несколько элементов для доступа к текущей выделенной области.  
  
 В зависимости от команды обработчик команд может потребоваться выделение в конструкторе моделей, обозреватель модели или активного окна.  
  
#### Для доступа к информации для выбора  
  
1.  <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> Класс определяет следующие члены, которые могут использоваться для доступа к текущей выделенной области.  
  
    |Член|Описание|  
    |----------|--------------|  
    |Метод <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsAnyDocumentSelectionCompartment%2A>|Возвращает `true` при выполнении любого из элементов, выбранных в конструкторе моделей фигуры секции; в противном случае — `false`.|  
    |Метод <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsDiagramSelected%2A>|Возвращает `true` Если схемы, выбранных в конструкторе моделей, в противном случае — `false`.|  
    |Метод <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleDocumentSelection%2A>|Возвращает `true` Если ровно один элемент, выбранный в конструкторе моделей, в противном случае — `false`.|  
    |Метод <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleSelection%2A>|Возвращает `true` Если ровно один элемент, выбранный в активном окне, в противном случае — `false`.|  
    |Свойство <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentDocumentSelection%2A>|Возвращает коллекцию только для чтения элементов, выбранных в конструкторе моделей.|  
    |Свойство <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentSelection%2A>|Возвращает коллекцию элементов, выбранных в активном окне только для чтения.|  
    |Свойство <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleDocumentSelection%2A>|Возвращает основной элемент выделения в конструкторе моделей.|  
    |Свойство <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleSelection%2A>|Возвращает основной элемент выделения в активном окне.|  
  
2.  <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet.CurrentDocView%2A> Свойства <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> класс предоставляет доступ к <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView> объект, который представляет окно конструктора моделей и предоставляет дополнительные права доступа выбранных элементов в конструкторе моделей.  
  
3.  Кроме того созданный код определяет свойство окна проводника средство и выбор свойство проводника в команде задать класс для доменного языка.  
  
    -   Свойство окна обозревателя средство возвращает экземпляр класса окна инструментов обозревателя для доменного языка. Класс окна инструмента обозревателя является производным от <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow> класса и представляет Обозреватель моделей для доменного языка.  
  
    -   `ExplorerSelection` Свойство возвращает элемент, выбранный в окне обозревателя моделей для доменного языка.  
  
## Определить, какое окно является активным  
 <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> Содержит интерфейс определяет члены, предоставляющие доступ к состоянию текущего выбора в оболочке. Можно получить <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> класс пакета или класс набора команд для доменного языка через объект `MonitorSelection` Свойства, определенные в базовом классе каждого. Класс пакета является производным от <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage> класса и класс набора команд является производным от <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> класса.  
  
#### Чтобы определить обработчик команды активен тип окна  
  
1.  <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.MonitorSelection%2A> Свойство <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> возвращает <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> объект, предоставляющий доступ к состоянию текущего выбора в оболочке.  
  
2.  <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService.CurrentSelectionContainer%2A> Свойства <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> интерфейс возвращает контейнер активного выделения, который может отличаться от активного окна.  
  
3.  Добавьте следующие свойства для команды set\-класс для вас доменного языка, чтобы определить, какой тип окна активен.  
  
    ```c#  
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
  
## Ограничение выбора  
 Добавление правила выбора, можно выбрать, какие элементы выбраны, когда пользователь выбирает элемент в модели. Например чтобы разрешить пользователю обрабатывать как единое целое число элементов, можно использовать правило выбора.  
  
#### Чтобы создать правило выбора  
  
1.  Создайте файл пользовательского кода в проекте DSL  
  
2.  Определите класс правило выбора, который является производным от <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules> класса.  
  
3.  Переопределение <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules.GetCompliantSelection%2A> метод класса правила выбора для применения критериев выбора.  
  
4.  Добавьте определение разделяемого класса для класса ClassDiagram в файл пользовательского кода.  
  
     `ClassDiagram` Класс является производным от <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram> класса и определен в созданный файл кода, Diagram.cs, в проекте DSL.  
  
5.  Переопределение <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> свойство `ClassDiagram` класса для возврата правило пользовательского выбора.  
  
     Реализация по умолчанию <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> свойство возвращает объект правила выделения, нельзя изменить выбор.  
  
### Пример  
 Следующий файл кода создает правило выбора, которое расширяет выборку для включения всех экземпляров каждого домена фигур, которые изначально была выбрана.  
  
```c#  
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
  
## См. также  
 <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>   
 <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage>   
 <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView>   
 <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow>   
 <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>   
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules>   
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>