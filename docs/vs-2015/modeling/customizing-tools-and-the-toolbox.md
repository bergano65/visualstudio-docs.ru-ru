---
title: Customizing Tools and the Toolbox | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.selectiondialog
- vs.dsltools.dsldesigner.selecticondialog
- vs.dsltools.dsldesigner.selectcursordialog
helpviewer_keywords:
- Domain-Specific Language, toolbox
ms.assetid: 2a0d03d7-ebc6-4458-b9f4-d2cb8418a62d
caps.latest.revision: 28
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2a5e2a46a2326c123d6b7b4e85fa29908ede9fc9
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299328"
---
# <a name="customizing-tools-and-the-toolbox"></a>Настройка элементов и панели элементов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Для тех элементов, которые пользователи смогут добавлять в свои модели, необходимо определить содержание панели элементов. Панель элементов может содержать два вида средств: средства элемента и средства подключения. В созданном конструкторе пользователь может выбрать средство элемента, чтобы перетащить фигуры на схему, и средство подключения, чтобы протянуть связи между фигурами. В целом средства элемента позволяют пользователям добавлять в модели экземпляры классов доменов, а средства подключения — экземпляры доменных связей.

 В этом разделе.

- [How the Toolbox is Defined](#ToolboxDef)

- [Настройка средств элемента](#customizing)

- [Creating Groups of Elements from a Tool](#groups)

- [Customizing Connection Tools](#connections)

## <a name="ToolboxDef"></a> How the toolbox is defined
 В Обозревателе DSL разверните узел "Редактор" и узлы под ним. Обычно при этом отрывается иерархия следующего вида:

```

Editor
     Toobox Tabs
        MyDsl          //a tab
           Tools
               ExampleElement      // an element tool
               ExampleRelationship // a connection tool

```

 В этой части Обозревателя DSL можно выполнять следующие действия.

- Создавать новые таблицы. Вкладки определяют заголовки разделов в панели элементов.

- Создавать новые средства.

- Копировать и вставлять средства.

- Перемещать средства вверх или вниз по списку.

- Удалять вкладки и средства.

> [!IMPORTANT]
> Чтобы добавить или вставить элементы в Обозреватель DSL, щелкните прародителя нового узла правой кнопкой мыши. For example, to add a tool, right-click the tab, and not the **Tools** node. To add a tab, right-click the **Editor** node.

 The **Toolbox Icon** property of every tool references a 16x16 bitmap file. These files are usually kept in the **Dsl\Resources** folder.

 The **Class** property of an element tool refers to a concrete domain class. По умолчанию средство будет создавать экземпляры данного класса. Тем не менее можно написать код, заставляющий средство создавать элементы или группы элементов другого типа.

 The **Connection Builder** property of a connection tool refers to a connection builder, which defines what types of elements the tool can connect, and what relationships it creates between them. Построители подключений определяются в виде узлов в Обозревателе DSL. Построители подключений создаются автоматически при определении доменных связей, но могут также настраиваться с помощью кода.

#### <a name="to-add-a-tool-to-the-toolbox"></a>Добавление средства в панель элементов

1. Средство элемента обычно создают после создания класса фигуры и его сопоставления с классом домена.

     Средство подключения обычно создают после создания класса соединителя и его сопоставления со ссылочным отношением.

2. In DSL Explorer, expand the **Editor** node and the **Toolbox Tabs** node.

     Right-click a toolbox tab node, and then click **Add New Element Tool** or **Add New Connection Tool**.

3. Set the **Toolbox Icon** property to refer to a 16x16 bitmap.

     If you want to define a new icon, create a bitmap file in Solution Explorer in the **Dsl\Resources** folder. The file should have the following property values: **Build Action** = **Content**; **Copy to Output Directory** = **Do not copy**.

4. **For an element tool:** Set the **Class** property of the tool to refer to a concrete domain class that is mapped to a shape.

     **For a connector tool:** Set the **Connection Builder** property of the tool to one of the items that are offered in the drop-down list. Построители подключений автоматически создаются при сопоставлении соединителя с доменной связью. Сразу после создания соединителя, как правило, выбирается соответствующий построитель подключений.

5. Чтобы проверить DSL, нажмите клавишу F5 или сочетание клавиш CTRL + F5 и откройте в экспериментальном экземпляре [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] пример файла модели. На панели элементов должно появиться новое средство. Перетащите его на схему, чтобы проверить, создает ли оно новый элемент.

     Если средство не появляется, остановите экспериментальный экземпляр [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. In the Windows **Start** menu, run **Reset the Microsoft Visual Studio 2010 Experimental Instance**. On the [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]**Build** menu, click **Rebuild Solution**. Затем проверьте DSL еще раз.

## <a name="customizing"></a> Customizing Element Tools
 По умолчанию средство создает один экземпляр указанного класса, но это можно изменять двумя описанными ниже способами.

- Определить директивы слияния элемента с другими классами, позволив им принимать новые экземпляры этого класса и создавать дополнительные ссылки при создании нового элемента. Например, можно разрешить пользователю оставить комментарий на другой элемент и тем самым создать между ними справочную ссылку.

     Эти настройки также влияют на процесс вставки и перетаскивания элемента.

     For more information, see [Customizing Element Creation and Movement](../modeling/customizing-element-creation-and-movement.md).

- Написать код, чтобы настроить средство на возможность создания групп элементов. Средство запускается методами из файла ToolboxHelper.cs, которые можно переопределить. For more information, see [Creating Groups of Elements from a Tool](#groups).

## <a name="groups"></a> Creating Groups of Elements from a Tool
 Каждое средство элемента содержит прототип элементов, которые оно должно создавать. По умолчанию, каждое средство элемента создает один элемент, но может также создавать группу объектов, связанных с одним средством. Для этого запустите средство с помощью класса <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype>, который содержит связанные элементы.

 Следующий пример взят из DSL, в котором есть тип "Транзистор". Каждый транзистор имеет три именованных контакта. Средство элемента для транзисторов хранит прототип, содержащий четыре элемента модели и три ссылки отношения. Когда пользователь перетаскивает средство на схему, создается экземпляр прототипа, который связывается с корнем модели.

 This code overrides a method that is defined in **Dsl\GeneratedCode\ToolboxHelper.cs**.

 For more information about customizing the model by using program code, see [Navigating and Updating a Model in Program Code](../modeling/navigating-and-updating-a-model-in-program-code.md).

```
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;

  public partial class CircuitsToolboxHelper
  {
    /// <summary>
    /// Toolbox initialization, called for each element tool on the toolbox.
    /// This version deals with each Component subtype separately.
    /// </summary>
    /// <param name="store"></param>
    /// <param name="domainClassId">Identifies the domain class this tool should instantiate.</param>
    /// <returns>prototype of the object or group of objects to be created by tool</returns>
    protected override ElementGroupPrototype CreateElementToolPrototype(Store store, Guid domainClassId)
    {
        if (domainClassId == Transistor.DomainClassId)
        {
            Transistor transistor = new Transistor(store);

            transistor.Base = new ComponentTerminal(store);
            transistor.Collector = new ComponentTerminal(store);
            transistor.Emitter = new ComponentTerminal(store);

            transistor.Base.Name = "base";
            transistor.Collector.Name = "collector";
            transistor.Emitter.Name = "emitter";

            // Create an ElementGroup for the Toolbox.
            ElementGroup elementGroup = new ElementGroup(store.DefaultPartition);
            elementGroup.AddGraph(transistor, true);
            // AddGraph includes the embedded parts

            return elementGroup.CreatePrototype();
        }
        else
        {
            return base.CreateElementToolPrototype(store, domainClassId);
}  }    }

```

## <a name="connections"></a> Customizing Connection Tools
 Как правило, средство элемента создается при создании нового класса соединителя. Кроме того, можно переопределить одно средство, разрешив типам и обеих сторон определять тип отношения. Например, можно определить одно средство подключения, которое может создавать как отношения типа "человек — человек", так и отношения типа "человек — город".

 Средства подключения вызывают построители подключения. Используйте построители подключения, чтобы указать, каким образом пользователи могут связывать элементы в сгенерированном конструкторе. Построители подключений указывают элементы, которые могут быть связаны, а также создаваемый между ними тип связи.

 При создании ссылочного отношения между доменными классами автоматически создается построитель подключения, который можно использовать при сопоставлении средства подключения. For more information about how to create connection tools, see [Configuring the Toolbox](../modeling/customizing-tools-and-the-toolbox.md).

 Построитель подключения по умолчанию можно изменить так, чтобы он мог справляться с другим диапазоном исходных и целевых типов, а также создавать различные типы отношений.

 Также, для построителей подключения можно написать пользовательский код, чтобы указать исходные и целевые классы для подключения, определить тип создаваемого подключения, и выполнить другие действия, связанные с созданием подключения.

### <a name="the-structure-of-connection-builders"></a>Структура построителей подключения
 Построители подключений содержат одну или несколько директив подключения связей, которые определяют доменные связи, а также исходные и целевые элементы. For example, in the Task Flow solution template, you can see the **CommentReferencesSubjectsBuilder** in the **DSL Explorer**. This connection builder contains one link connect directive named **CommentReferencesSubjects**, which is mapped to the domain relationship **CommentReferencesSubjects**. Эта директива подключения связи содержит директиву исходной роли, указывающую на класс домена `Comment`, и директиву целевой роли, указывающую на класс домена `FlowElement`.

### <a name="using-connection-builders-to-restrict-source-and-target-roles"></a>Использование построителей подключений для ограничения ограниченным исходных и целевых ролей
 Построители подключений можно использовать для ограничения вхождения некоторых классов в исходную или в целевую роль определенной доменной связи. Например, у вас есть базовый класс домена, имеющий доменную связь с другим классом домена, но вы не хотите, чтобы все производные этого базового класса получали в этой связи те же самые роли. In the Task Flow solution, there are four concrete domain classes (**StartPoint**, **EndPoint**, **MergeBranch**, and **Synchronization**) that inherit directly from the abstract domain class **FlowElement**, and two concrete domain classes (**Task** and **ObjectInState**) that inherit indirectly from it. There is also a **Flow** reference relationship that takes **FlowElement** domain classes in both its source role and target role. However, an instance of an **EndPoint** domain class should not be the source of an instance of a **Flow** relationship, nor should an instance of a **StartPoint** class be the target of an instance of a **Flow** relationship. The **FlowBuilder** connection builder has a link connect directive named **Flow** that specifies which domain classes can play the source role (**Task**, **MergeBranch**, **StartPoint**, and **Synchronization**) and which can play the target role(**MergeBranch**, **Endpoint**, and **Synchronization**).

### <a name="connection-builders-with-multiple-link-connect-directives"></a>Построители подключений с несколькими директивами подключения связи
 К построителю подключений можно добавить несколько директив подключения связи. This can help you hide some of the complexities of the domain model from users and keep the **Toolbox** from getting too cluttered. К одному построителю подключений можно добавить директивы подключения связи для нескольких различных отношений домена. При этом доменные связи следует объединять в том случае, если они выполняют примерно одинаковую функцию.

 In the Task Flow solution, the **Flow** connection tool is used to draw instances of both the **Flow** and the **ObjectFlow** domain relationships. The **FlowBuilder** connection builder has, in addition to the **Flow** link connect directive described earlier, two link connect directives named **ObjectFlow**. These directives specify that an instance of an **ObjectFlow** relationship may be drawn between instances of the **ObjectInState** domain class, or from an instance of an **ObjectInState** to an instance of a **Task**, but not between two instances of a **Task**, or from an instance of a **Task** to an instance of an **ObjectInState**. However, an instance of a **Flow** relationship may be drawn between two instances of a **Task**. If you compile and run the Task Flow solution, you can see that drawing a **Flow** from an instance of an **ObjectInState** to an instance of a **Task** creates an instance of an **ObjectFlow**, but drawing a **Flow** between two instances of a **Task** creates an instance of a **Flow**.

### <a name="custom-code-for-connection-builders"></a>Пользовательский код для построителей подключения
 В пользовательском интерфейсе имеются четыре флажка, определяющие различные типы настройки построителей подключений:

- the **Custom accept** check box on a source or target role directive

- the **Custom connect** check box on a source or target role directive

- the **Uses custom connect** check box on a connect directive

- the **Is Custom** property of the connection builder

  Чтобы указать эти настройки, необходимо предоставить определенный программный код. Чтобы узнать, какой код необходимо предоставить, установите один их этих флажков, нажмите кнопку "Преобразовать все шаблоны" и постройте собственное решение. В результате будет получено сообщение об ошибке. Дважды щелкните сообщение об ошибке, чтобы увидеть комментарий с описанием кода, который необходимо добавить.

> [!NOTE]
> Чтобы добавить пользовательский код, создайте определение разделяемого класса в файле кода отдельно от файлов кода, находящихся в папках GeneratedCode. Чтобы не потерять свою работу, не изменяйте созданные файлы кода. For more information, see [Overriding and Extending the Generated Classes](../modeling/overriding-and-extending-the-generated-classes.md).

#### <a name="creating-custom-connection-code"></a>Создание пользовательского кода подключения
 In each link connect directive, the **Source role directives** tab defines from what types you can drag. Similarly, the **Target role directives** tab defines to what types you can drag. For each type, you can further specify whether to allow the connection (for that link connect directive) by setting the **Custom Accept** flag and then supplying the extra code.

 Также можно настроить действия, происходящие после выполнения подключения. Например, можно настроить только случай перетаскивания в определенный класс, все случаи, когда приоритетное значение имеет одна директива подключения связи, или весь построитель подключения FlowBuilder. Для каждого из этих вариантов можно установить пользовательские флажки на соответствующем уровне. При преобразовании всех шаблонов и попытке построить решение вы получите сообщения об ошибках с комментариями к созданному коду. В этих комментариях указывается, что необходимо предоставить.

 В примере "Схема компонентов" построитель подключения для доменной связи "Подключение" ограничивает подключения, которые могут быть установлены между портами. На следующей иллюстрации показано, что подключения можно установить только от элементов `OutPort` к элементам `InPort`, но компоненты можно вкладывать друг в друга.

 **Connection Coming in to an OutPort from a Nested Component**

 ![Connection Builder](../modeling/media/connectionbuilder-3.png "ConnectionBuilder_3")

 В связи с этим необходимо указать, что подключение может идти от вложенного компонента к типу OutPort. To specify such a connection, you set **Uses Custom Accept** on the **InPort** type as source role and the **OutPort** type as target role in the **DSL Details** window as shown in the following illustrations:

 **Link Connect Directive in DSL Explorer**

 ![Connection builder image](../modeling/media/connectionbuilder-4a.png "ConnectionBuilder_4a")

 **Link Connect Directive in DSL Details Window**

 ![](../modeling/media/connectionbuilder-4b.png "ConnectionBuilder_4b")

 После этого в класс ConnectionBuilder необходимо предоставить методы:

```
  public partial class ConnectionBuilder
  {
    /// <summary>
    /// OK if this component has children
    /// </summary>
    private static bool CanAcceptInPortAsSource(InPort candidate)
    {
       return candidate.Component.Children.Count > 0;
    }

    /// <summary>
    /// Only if source is on parent of target.
    /// </summary>
    private static bool CanAcceptInPortAndInPortAsSourceAndTarget                (InPort sourceInPort, InPort targetInPort)
    {
      return sourceInPort.Component == targetInPort.Component.Parent;
    }
// And similar for OutPorts…
```

 For more information about customizing the model by using program code, see [Navigating and Updating a Model in Program Code](../modeling/navigating-and-updating-a-model-in-program-code.md).

 Подобный код можно использовать, например, для того, чтобы запретить пользователям создавать циклы со связями между родительскими и дочерними объектами. Эти ограничения считаются жесткими, потому что пользователи не смогут их нарушать. Можно создавать мягкие проверки достоверности, которые пользователи смогут временно обходить, создавая недопустимые конфигурации без возможности сохранения.

### <a name="good-practice-in-defining-connection-builders"></a>Рекомендации по определению построителей подключений
 Чтобы создаваемые типы отношений были концептуально связаны, настраивайте только один построитель подключений. В примере с задачей потока (Task Flow) для создания потоков между задачами, а также между задачами и объектами используется один и тот же построитель. В то же время использование одного и того же построителя для создания отношений между комментариями и задачами может создавать путаницу.

 Определяя построитель подключений для нескольких типов отношений, обязательно убедитесь, что он не может сопоставить больше одного типа из одной той же пары исходных и целевых объектов. В противном случае результаты будут непредсказуемы.

 Пользовательский код используется для применения жестких ограничений. Подумайте, не стоит ли разрешить пользователям временное создание недопустимых подключений. Если такую возможность необходимо предоставить, ограничения можно изменить таким образом, чтобы эти подключения не проверялись до тех пор, пока пользователи не попытаются сохранить изменения.

## <a name="see-also"></a>См. также раздел
 [Customizing Element Creation and Movement](../modeling/customizing-element-creation-and-movement.md) [Customizing Copy Behavior](../modeling/customizing-copy-behavior.md) [How to: Add a Drag-and-Drop Handler](../modeling/how-to-add-a-drag-and-drop-handler.md) [Navigating and Updating a Model in Program Code](../modeling/navigating-and-updating-a-model-in-program-code.md)
