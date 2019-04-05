---
title: Редактирование схем последовательностей UML с помощью UML API | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML activity diagrams, programming
ms.assetid: 8cdd0203-85ef-4c62-9abc-da4cb26fa504
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1c71becfb04115faefe88d5018c238ead38e4c88
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58993665"
---
# <a name="edit-uml-sequence-diagrams-by-using-the-uml-api"></a>Редактирование схем последовательностей UML с помощью API UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Взаимодействие — это последовательность сообщений между набором жизненных циклов. Взаимодействие отображается на схеме последовательностей UML.  
  
 Полные сведения об интерфейсе API см. в разделе <xref:Microsoft.VisualStudio.Uml.Interactions?displayProperty=fullName>.  
  
 Более общие сведения о создании команд и обработчиков жестов для схем UML, см. в разделе [определение команды меню на схеме моделирования](../modeling/define-a-menu-command-on-a-modeling-diagram.md).  
  
## <a name="basic-code"></a>Базовый код  
  
### <a name="namespace-imports"></a>Импорт пространства имен  
 Необходимо использовать следующие операторы `using`.  
  
```  
using Microsoft.VisualStudio.Uml.Classes;  
   // for basic UML types such as IPackage  
using Microsoft.VisualStudio.Uml.Interactions;  
   // for interaction types  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
   // to create elements and use additional functions  
```  
  
 При создании команд меню и обработчиков жестов вам также потребуется следующее:  
  
```  
using System.ComponentModel.Composition;   
   // for Import and Export  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
   // for ICommandExtension  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
   // for diagrams and context  
```  
  
 Дополнительные сведения см. в разделе [определение команды меню на схеме моделирования](../modeling/define-a-menu-command-on-a-modeling-diagram.md).  
  
### <a name="getting-the-context"></a>Получение контекста  
 При редактировании взаимодействия как части команды или обработчика жестов на схеме последовательностей вы можете получить ссылку на контекст. Пример:  
  
```  
[SequenceDesignerExtension]  
[Export(typeof(ICommandExtension))]    
public class MySequenceDiagramCommand : ICommandExtension  
{  
    [Import]  
    public IDiagramContext Context { get; set; }  
    public void QueryStatus (IMenuCommand command)  
    {  
      ISequenceDiagram sequenceDiagram =   
          Context.CurrentDiagram as ISequenceDiagram;  
         ...  
```  
  
### <a name="generated-and-uml-sequence-diagrams"></a>Созданные схемы последовательностей и схемы последовательностей UML  
 Существует два вида схем последовательностей: те, которые были созданы вручную в UML-проекте моделирования, и те, которые были созданы из кода программы. Используйте свойство `UmlMode` для определения имеющейся схемы последовательностей.  
  
> [!NOTE]
>  Это свойство возвращает значение false только для схем последовательностей, созданных из кода с помощью Visual Studio 2013 и более ранних версий. Сюда входят созданные из кода схемы последовательностей, перенесенные из Visual Studio 2013 и более ранних версий. Эта версия Visual Studio не поддерживает создание новых схем последовательностей.  
  
 Например, если нужно создать команду меню, видимую только на схемах последовательностей UML, метод `QueryStatus()` может включать в себя следующий оператор:  
  
```  
command.Enabled = command.Visible =   
      sequenceDiagram != null && sequenceDiagram.UmlMode;  
```  
  
 На созданной схеме последовательностей используются практически те же жизненные циклы, сообщения и другие элементы, что и на схеме последовательностей UML. В модели UML хранилище моделей имеет корень, который представляет собой модель, владеющую всеми остальными элементами. Однако созданное взаимодействие существует в своем собственном хранилище моделей, имеющем неопределенный (NULL) корень.  
  
```  
IModel rootModel = sequenceDiagram.ModelStore.Root;  
    // !sequenceDiagram.UmlMode == (rootModel == null)  
```  
  
## <a name="to-create-and-display-an-interaction"></a>Создание и отображение взаимодействия  
 Создайте взаимодействие в качестве дочернего элемента пакета или модели.  
  
 Например, если вы разрабатываете команду, которая может выполняться на пустой схеме последовательностей, следует всегда начинать с проверки наличия этого взаимодействия.  
  
```  
public void Execute (IMenuCommand command)  
{  
    ISequenceDiagram sequenceDiagram =   
         Context.CurrentDiagram as ISequenceDiagram;  
    if (sequenceDiagram == null) return;  
    // Get the diagram's interaction:  
    IInteraction interaction = sequenceDiagram.Interaction;  
    // A new sequence diagram might have no interaction:  
    if (interaction == null)  
    {  
       // Get the home package or model of the diagram:  
       IPackage parentPackage = sequenceDiagram.GetObject<IPackage>();  
       interaction = parentPackage.CreateInteraction();  
       // Display the interaction on the sequence diagram:  
       sequenceDiagram.Bind(interaction);  
    }   
```  
  
## <a name="updating-an-interaction-and-its-layout"></a>Обновление взаимодействия и его структуры  
 При обновлении взаимодействия всегда нужно завершать операцию обновлением структуры с помощью одного из следующих методов:  
  
- `ISequenceDiagram.UpdateShapePositions()` регулирует положение фигур, которые недавно вставленных или перемещенных и их соседних фигуры.  
  
- `ISequenceDiagram.Layout([SequenceDiagramLayoutKinds])` перерисовывает всю схему. Параметр можно использовать для задания изменения положения жизненных циклов и/или сообщений.  
  
  Это особенно важно при вставке новых элементов или перемещении существующих элементов. Они не будут находиться в правильном положении на схеме, пока вы не выполните одну из этих операций. Одну из этих операций необходимо вызывать лишь однократно в конце последовательности изменений.  
  
  Чтобы не вводить в заблуждение пользователя, выполняющего отмену после данной команды, используйте `ILinkedUndoTransaction` для ограничения изменений, а в конце используйте операцию `Layout()` или `UpdateShapePositions()`. Пример:  
  
```  
using (ILinkedUndoTransaction transaction = LinkedUndoContext.BeginTransaction("create loop"))  
{  
  Interaction.CreateCombinedFragment(InteractionOperatorKind.Loop, messages);  
  Diagram.UpdateShapePositions();  
  transaction.Commit();  
}  
```  
  
 Чтобы использовать `ILinkedUndoTransaction`, необходимо сделать это объявление в классе:  
  
```  
[Import] ILinkedUndoContext LinkedUndoContext { get; set; }  
```  
  
 Дополнительные сведения см. в разделе [обновлений модели UML ссылку с помощью транзакций](../modeling/link-uml-model-updates-by-using-transactions.md).  
  
## <a name="building-an-interaction"></a>Построение взаимодействия  
  
### <a name="to-create-lifelines"></a>Создание жизненных циклов  
  
```  
ILifeline lifeline = interaction.CreateLifeline();  
```  
  
 Жизненный цикл представляет подключаемый элемент, то есть экземпляр типа. Например, если взаимодействие используется, чтобы показать, как компонент делегирует входящие сообщения своим внутренним частям, жизненные циклы могут представлять порты и части компонента.  
  
```  
foreach (IConnectableElement part in   
            component.Parts  
           .Concat<IConnectableElement>(component.OwnedPorts))  
{  
   ILifeline lifeline = interaction.CreateLifeline();  
   lifeline.Represents = part;  
}  
```  
  
 Кроме того, если взаимодействие показывает произвольный набор объектов, можно создать свойство или другой элемент `IConnectableElement` в самом взаимодействии:  
  
```  
ILifeline lifeline = interaction.CreateLifeline();  
IProperty property1 = interaction.CreateProperty();  
property1.Type = model.CreateInterface();  
property1.Type.Name = "Type 1";  
lifeline.Represents = property1;  
```  
  
 Можно также задать имя и тип жизненного цикла, не связывая его с подключаемым элементом.  
  
```  
ILifeline lifeline = interaction.CreateLifeline();  
lifeline.Name = "c1";  
lifeline.SetInstanceType("Customer");  
System.Diagnostics.Debug.Assert(  
           lifeline.GetDisplayName() == "c1:Customer"  );  
```  
  
### <a name="to-create-messages"></a>Создание сообщений  
 Чтобы создать сообщение, необходимо определить точки вставки в исходном и целевом жизненных циклах. Пример:  
  
```  
interaction.CreateMessage( sourceInsertionPoint,   
                           targetInsertionPoint,   
                           MessageKind.Complete,   
                           MessageSort.ASynchCall)  
```  
  
 Чтобы создать сообщение, которое имеет неопределенный источник или неопределенную цель, используйте следующее:  
  
```  
interaction.CreateLostFoundMessage(MessageKind.Found, insertionPoint);  
```  
  
 Существует несколько сообщений, которые можно использовать для определения точек вставки во всех ключевых точках жизненного цикла.  
  
|Метод для ILifeline|Используется для вставки в данной точке|  
|-------------------------|------------------------------------|  
|`FindInsertionPointAtTop()`|Верх жизненного цикла.|  
|`FindInsertionPointAtBottom()`|Низ жизненного цикла.|  
|`FindInsertionPointAfterMessage`<br /><br /> `(IMessage previous)`|Точка сразу после заданного сообщения.|  
|`FindInsertionPointAfterExecutionSpecification`<br /><br /> `(IExecutionSpecification previous)`|Точка может быть либо на жизненном цикле, либо на родительском блоке спецификации выполнения.|  
|`FindInsertionPointAfterInteractionUse`<br /><br /> `(IInteractionUse previous)`|Точка, следующая за использованием взаимодействия.|  
|`FindInsertionPointAfterCombinedFragment`<br /><br /> `(ICombinedFragment previous)`|Точка, следующая за объединенным фрагментом.|  
|`FindInsertionPoint(IExecutionSpecification block)`|Верх блока выполнения.|  
|`FindInsertionPoint(IInteractionOperand fragment)`|Верх операнда объединенного фрагмента.|  
  
 При создании сообщений необходимо избегать определения сообщения, которое будет накладываться на другое сообщение.  
  
### <a name="to-create-combined-fragments-and-interaction-uses"></a>Создание объединенных фрагментов и вариантов использования взаимодействия  
 Объединенные фрагменты и варианты использования взаимодействия можно создать, указав точку вставки на каждом жизненном цикле, который должен охватываться этим элементом. Избегайте задания набора точек, которые бы накладывались на существующее сообщение или существующий фрагмент.  
  
```  
Interaction.CreateCombinedFragment(InteractionOperatorKind.Loop,   
  Interaction.Lifelines.Select(lifeline => lifeline.FindInsertionPointAtTop()));  
Interaction.CreateInteractionUse(  
  Interaction.Lifelines.Select(lifeline => lifeline.FindInsertionPointAtTop()));  
```  
  
 Можно также создать объединенный фрагмент, охватывающий существующий набор сообщений. Источником сообщений должен быть один жизненный цикл или блок выполнения.  
  
```  
ICombinedFragment cf = Interaction.CreateCombinedFragment(  
  InteractionOperatorKind.Loop,  
  Interaction.Lifelines.First().GetAllOutgoingMessages());  
```  
  
 Объединенный фрагмент всегда создается с одним операндом. Чтобы создать новый операнд, необходимо указать существующий операнд, а также задать место вставки — до или после:  
  
```  
// Create an additional operand before the first  
cf.CreateInteractionOperand(cf.Operands.First(), false);  
// Create an additional operand after the last:  
cf.CreateInteractionOperand(cf.Operands.Last(), true);  
```  
  
## <a name="troubleshooting"></a>Устранение неполадок  
 Фигуры будут отображаться в неправильных положениях, если изменения не завершены операцией `UpdateShapePositions()` или `Layout()`.  
  
 Большинство проблем вызвано несогласованностью точек вставки, что приводит к наложению новых сообщений или фрагментов на другие. Симптомы могут заключаться в том, что изменение не выполняется или выдается исключение. Исключение не может выдаваться до выполнения операции `UpdateShapePositions()` или `Layout()`.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Uml.Interactions?displayProperty=fullName>   
 [Расширение моделей и схем UML](../modeling/extend-uml-models-and-diagrams.md)   
 [Определение команды меню на схеме моделирования](../modeling/define-a-menu-command-on-a-modeling-diagram.md)   
 [Определение настраиваемого элемента панели элементов моделирования](../modeling/define-a-custom-modeling-toolbox-item.md)   
 [Определение ограничений проверки для моделей UML](../modeling/define-validation-constraints-for-uml-models.md)   
 [Программирование с UML API](../modeling/programming-with-the-uml-api.md)
