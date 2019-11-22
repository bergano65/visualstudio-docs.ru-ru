---
title: 'UML Activity Diagrams: Guidelines | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML diagrams, activity
- diagrams - modeling, activity
- diagrams - modeling, UML activity
- activity diagrams
- UML, activity diagrams
ms.assetid: fe5dbe96-79ab-483a-b9bc-44d0d1d3efc2
caps.latest.revision: 50
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 692859008891439e4af3d751306bfd3ee6d351e8
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298988"
---
# <a name="uml-activity-diagrams-guidelines"></a>UML-схемы деятельности: рекомендации
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В Visual Studio можно создавать схемы активности, описывающие бизнес-процесс или программный алгоритм как поток работы, состоящий из ряда действий. Эти действия могут выполняться людьми, программными компонентами или устройствами. For a video demonstration, see: [Capture Business Workflows by using Activity Diagrams](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-4-capture-business-workflows).

 Чтобы узнать, какие версии Visual Studio поддерживают эту функцию, см. раздел [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 To create a UML activity diagram, on the **Architecture** menu, click **New UML or Layer Diagram**.

 Схемы деятельности можно использовать для различных целей:

- Для описания бизнес-процесса или потока работы, в которых участвуют пользователи и система. For more information, see [Model user requirements](../modeling/model-user-requirements.md).

- для описания шагов, выполняемых в варианте использования For more information, see [UML Use Case Diagrams: Guidelines](../modeling/uml-use-case-diagrams-guidelines.md).

- для описания метода, функции или операции программного обеспечения For more information, see [Model your app's architecture](../modeling/model-your-app-s-architecture.md).

  Создание схемы деятельности помогает улучшить процесс. Если схема существующего процесса оказывается очень сложной, можно подумать, как ее упростить.

  For reference information about the elements on activity diagrams, see [UML Activity Diagrams: Reference](../modeling/uml-activity-diagrams-reference.md).

## <a name="Relationships"></a> Relationship to Other Diagrams
 Создавая схему активности для описания бизнес-процесса или способа применения системы пользователями, можно создать также схему вариантов использования, демонстрирующую различные точки зрения на одну и ту же информацию. На схеме вариантов использования действия изображаются как варианты использования. Присвойте вариантам использования имена, совпадающие с именами соответствующих действий. Представление вариантов использования позволяет выполнять следующее:

- с помощью отношения Includes показывать на одной схеме, каким образом большие действия или варианты использования формируются из меньших;

- явно привязывать каждое из действий или вариантов использования к пользователям или внешним системам, участвующим в его выполнении;

- проводить границы вокруг действий или вариантов использования, поддерживаемых системой или основными ее компонентами.

  Также можно использовать схему активности для подробного описания операции программы.

  На схеме активности можно показать поток данных, передаваемых между действиями. See the section on [Describing Data Flow](#DataFlows). При этом схема активности не описывает структуру данных. Для этой цели можно создать UML-схему классов. For information see [UML Class Diagrams: Guidelines](../modeling/uml-class-diagrams-guidelines.md).

## <a name="BasicSteps"></a> Basic Steps for Drawing Activity Diagrams
 Detailed steps for creating any of the modeling diagrams are described in [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md).

#### <a name="to-draw-an-activity-diagram"></a>Создание схемы активности

1. On the **Architecture** menu, click **New UML or Layer Diagram**.

2. Under **Templates**, click **UML Activity Diagram**.

3. Назовите схему.

4. In **Add to Modeling Project**, select an existing modeling project in your solution, or **Create a New Modeling Project**.

#### <a name="to-draw-elements-on-an-activity-diagram"></a>Создание элементов на схеме активности

1. Перетащите элементы из панели элементов на схему.

     Начните с размещения на схеме основных действий, соедините их и закончите добавлением таких элементов, как начальные и конечные узлы.

    > [!NOTE]
    > Нельзя перетаскивать на схему существующие элементы из обозревателя моделей UML.

2. Чтобы подключить элементы, выполните следующие действия:

    1. In the **Activity Diagram** toolbox, click **Connector**.

    2. Щелкните на схеме исходный элемент.

    3. Щелкните целевой элемент.

        > [!NOTE]
        > Чтобы использовать один и тот же элемент несколько раз, дважды щелкните его на панели элементов.

#### <a name="to-move-an-activity-to-another-package"></a>Перемещение действия в другой пакет

- In **UML Model Explorer**, drag the activity into a package.

     \- или -

- In **UML Model Explorer**, right-click the activity and click **Cut**. Then right-click the package and click **Paste**.

    > [!NOTE]
    > Это действие отобразится в обозревателе моделей UML только при добавлении первого элемента на схему.

## <a name="SimpleControlFlow"></a> Describing Control Flow
 Схема активности описывает бизнес-процесс или программный алгоритм как последовательность действий. Стрелки-соединители показывают, как управление последовательно передается от одного действия к другому. Обычно действие может начаться только после завершения предыдущего действия.

 На следующем рисунке приведен пример, как можно показывать последовательность действий с помощью действий, соединителей, ветвей и циклов. Более подробно элементы описаны в следующих разделах.

 ![A simple activity diagram](../modeling/media/uml-actguidectrl.png "UML_ActGuideCtrl")

 Activity diagrams use **Actions** and **Connectors** to describe your system or application as a series of actions with the control flowing sequentially from one action to the next.

- Create an **Action** (1) for each major task that is performed by a user, the system, or both in collaboration.

  > [!NOTE]
  > Постарайтесь описать процесс или алгоритм всего несколькими действиями. You can use **Call Behavior Actions** to define each action in more detail in a separate diagram, as described in [Describing Sub-activities with Call Behavior Actions](#Subactivities).

- Убедитесь, что заголовок каждого действия четко показывает, зачем оно нужно.

- Link the actions in sequence with **Connectors** (2).

- Каждое действие заканчивается до начала следующего действия в потоке управления. If you want to describe actions that overlap, use a **Fork Node** as described in the section [Concurrent Flows](#Concurrent).

  Схема описывает последовательность действий, но не показывает, каким образом эти действия выполняются и как управление передается от одного действия к следующему. Если с помощью схемы изображается бизнес-процесс, управление может передаваться, например, при отправке сообщения электронной почты одним человеком другому. Если с помощью схемы иллюстрируется система программного обеспечения, управление может передаваться при нормальном потоке выполнения от одного оператора к другому.

### <a name="describing-decisions-and-loops"></a>Описание решений и циклов

- Use a **Decision Node** (3) to indicate a point where the outcome of a decision dictates the next step. Можно добавить любое количество исходящих путей.

- Если с помощью схемы активности определяется часть приложения, следует определить условия (4), чтобы было понятно, когда следует использовать каждый из путей. Right-click the connector, click **Properties**, and in the **Properties** window, type a value for the **Guard** field.

- Не всегда необходимо определять условия. Например, если схема активности используется для описания бизнес-процесса или протокола взаимодействия, ветвь определяет диапазон параметров, доступных для пользователя или взаимодействующих компонентов.

- Use a **Merge Node** (5) to bring together two or more alternative flows that branched at a **Decision Node**.

    > [!NOTE]
    > You should use a **Merge Node** to bring together alternative flows, instead of bringing the flows together at an action. In the example, it would not be correct to connect from the decision node directly back to **Choose Menu Item**. Это связано с тем, что действие не запускается, пока потоки управления не поступят во все входящие соединители. Таким образом, объединять в действии следует только параллельные потоки. For more information, see [Concurrent Flows](#Concurrent).

- Циклы можно описывать с помощью ветвей, как показано в примере.

    > [!NOTE]
    > Старайтесь вкладывать циклы структурированно, как в коде программы. Если вы описываете существующий бизнес-процесс, это может показать некоторые возможности для его улучшения.

### <a name="starting-the-activity"></a>Начало активности
 Точки входа в активность можно указывать двумя способами:

- **Initial Node**

     Create one **Initial Node** (6) to indicate the first action of the activity.

     Этот метод лучше всего работает при описании вложенных активностей или в случаях, когда прямо указывать инициатора активности не нужно. Например, активность "Заказ еды" определенно начинается с того, что клиент проголодался.

- **Accept Event Node**

     Create **Accept Event Nodes**, as described in the section [Concurrent Flows](#Concurrent), to indicate the start of a thread that responds to a particular event, such as a user input. Не предоставляйте входящий в узел поток. Пропуск входящего потока означает, что поток запускается при каждом возникновении события.

     Этот метод пригодится в том случае, если нужно описать ответ на определенное внешнее событие.

### <a name="ending-the-activity"></a>Завершение действия
 Use an **Activity Final Node** (7) to indicate the end of an activity.

- When a thread of control reaches an **Activity Final Node**, all the activity's concurrent actions and sub-activities terminate.

- Можно использовать несколько конечных узлов, чтобы сократить число соединителей.

### <a name="interrupting-the-activity"></a>Прерывание действия
 Чтобы описать, как можно прерывать обычный поток действий, например если пользователь решает отменить процесс, можно создать узел приема события, прослушивающий это событие. For more information, see the section [Concurrent Flows](#Concurrent). Создайте поток управления между этим узлом и конечным узлом действия (7).

### <a name="swimlanes"></a>Дорожки
 Иногда части действия удобно разбить на области, соответствующие различным объектам или бизнес-ролям, выполняющим действия. These areas are conventionally arranged in columns and are called *swimlanes*.

- Use lines or rectangles from the **Simple Shapes** section of the Toolbox to draw swimlanes or other areas.

- To label each swimlane, create a comment and set its **Transparent** property to **True**.

  Простые фигуры не являются частью модели UML и не отображаются в обозревателе моделей UML.

## <a name="DataFlows"></a> Describing Data Flow
 Данные, передающиеся в действие или из него, можно описать одним из двух способов.

- Use an **Object Node**. Это простейший способ описания информации, передаваемой между действиями. Узел объекта похож на переменную в программе. Он представляет элемент, хранящий одно или несколько значений, которые передаются от одного действия к другому.

- Use an **Output Pin** and an **Input Pin**. Этот метод позволяет отдельно описывать выходные данные одного действия и входные данные другого. Закрепления похожи на параметры в программе. Закрепления представляют порты входа объектов в действие и выхода из него.

    > [!NOTE]
    > For an overview of the elements used in this section, see the Data Flows section of the topic see [UML Activity Diagrams: Reference](../modeling/uml-activity-diagrams-reference.md).

### <a name="describing-data-flow-with-object-nodes"></a>Описание потока данных с помощью узлов объектов
 Большинство потоков управления передает данные. Например выходной поток действия "Клиент предоставляет сведения" передает ссылку на адрес доставки.

 Если нужно описать эти данные на схеме, можно заменить соединитель узлом объекта и двумя соединителями, как показано на приведенном ниже рисунке.

 ![Object nodes can show data passed between actions](../modeling/media/uml-actguidedata.png "UML_ActGuideData")

 Обратите внимание, что прямоугольники с закругленными углами, например "Отправить товары", представляют действия, в которых происходит обработка. Прямоугольники с прямыми углами, например "Адрес поставки", представляют потоки объектов из одного действия в другое.

 Присвойте узлу объекта имя, отражающее роль узла как передаточного звена или буфера для объектов, передаваемых между действиями.

 You can set the **Type** of the object node in the Properties window. Это может быть примитивный тип, например "Целое число", либо класс, интерфейс или перечисление, определенные на схеме классов. Например, можно создать класс "Адрес поставки" с атрибутами "Улица", "Город" и так далее, связав его с другим классом под названием "Клиент". For more information, see [UML Class Diagrams: Guidelines](../modeling/uml-class-diagrams-guidelines.md).

> [!NOTE]
> If you type the name of a type that has not yet been defined, an item will be added under **Unspecified Types** in UML Model Explorer. Если после этого определить тип с таким именем на схеме классов, необходимо сбросить тип узла объекта, чтобы он ссылался на новый тип.

#### <a name="buffering-data-in-object-nodes"></a>Буферизация данных в узлах объектов
 Узел объекта может выступать в качестве буфера для нескольких объектов. На следующем рисунке поток управления показывает, что пользователь может пройти цикл [выбрать еще] (1) много раз, а узел объекта "Выбранные элементы меню" (2) накапливает решения пользователя. Наконец, когда пользователь завершает выбор, управление передается действию "Подтвердить заказ" (3), которое принимает полный список решений из буфера "Выбранные элементы меню".

 ![Buffering data in object nodes](../modeling/media/uml-actguidebuffer.png "UML_ActGuideBuffer")

 Чтобы указать способ хранения элементов в буфере, настройте указанные ниже свойства узла объекта.

- Set the **Ordering** property:

  - **Unordered** to specify a random or unspecified order. (по умолчанию).

  - **Ordered** to specify an order according to a specific key.

  - **Fifo** to specify an order of first-in, first-out.

  - **Lifo** to specify an order of last-in, first-out.

- Set the **Upper Bound** property to specify the maximum number of objects that can be contained in the buffer. Значение по умолчанию — *. Это означает отсутствие ограничений.

### <a name="describing-data-flow-with-input-and-output-pins"></a>Описание потока данных с помощью закреплений ввода и вывода
 Use an **Output Pin** and an **Input Pin** to separately describe the outputs from one action and the inputs to another.

 ![Input and output pins are action parameters](../modeling/media/uml-actguidepins.png "UML_ActGuidePins")

 To create a pin, click **Input Pin** or **Output Pin** on the toolbox and then click an action. Затем можно переместить закрепление по периметру действия и изменить его имя. You can create input and output pins on any kind of action, including **Call Behavior Actions**, **Call Operation Actions**, **Send Signal Actions**, and **Accept Event Actions**.

 Соединитель между двумя закреплениями представляет поток объектов (точно так же, как потоки в узел объекта и из него).

 Присваивайте закреплениям имена, указывающие на роль создаваемых или принимаемых ими объектов, например имена параметров.

 You can set the type of objects transmitted in the **Type** property. Это должен быть тип, созданный на UML-схеме классов.

 Объекты, передаваемые между соединенными закреплениями, должны быть каким-либо образом совместимы. Например, объекты, создаваемые закреплением вывода, могут принадлежать к производному типу типа закрепления ввода.

 Также можно указать, что поток объектов включает преобразование, которое изменяет данные из типа закрепления вывода в тип закрепления ввода. Наиболее распространенные преобразования такого рода просто извлекают подходящую часть из большего типа. В примере на рисунке подразумевается преобразование, которое извлекает адрес доставки из сведений о заказе.

## <a name="Details"></a> Defining an Action in More Detail
 Наряду с выбором имени, позволяющего описать получаемый действием результат, существуют и другие способы описать действие более подробно.

- Write a more detailed description in the **Body** property. Например, можно написать фрагмент программного кода или псевдокода или дать полное описание получаемых результатов.

- Заменить действие действием вызова поведения и подробно описать его поведение на отдельной схеме активности. See [Describing Sub-activities with Call Behavior Actions](#Subactivities).

- Set the action's **Local Postconditions** and **Local Preconditions** properties to describe its outcome in more specific detail. For more information, see [Defining Postconditions and Preconditions](#Postcondition).

### <a name="Subactivities"></a> Describing Sub-activities with Call Behavior Actions
 Подробно описать поведение действия можно с помощью отдельной схемы активности. Вызываемое поведение — это схема активности, представленная на основной схеме активности действием вызова поведения. Действие вызова поведения позволяет также описать поведение, которое используется в разных активностях, и не создавать одну и ту же вложенную активность несколько раз.

 Схема 1 на приведенном ниже рисунке демонстрирует активность с действием вызова поведения, а схема 2 — вложенную активность, отображающую вызываемое поведение.

 ![A separate activity diagram shows detailed actions](../modeling/media/uml-actguidedetail.png "UML_ActGuideDetail")

##### <a name="to-describe-a-sub-activity-with-a-call-behavior-action"></a>Описание вложенной активности с помощью действий вызова поведения

1. To create the diagram for the sub-activity, in **Solution Explorer**, right-click your modeling project, point to **Add**, and then click **New Item**.

2. In the **Add New Item** dialog box, under **Templates** click **Activity Diagram** and in the **Name** box type the name that you plan to give your **Call Behavior Action**.

3. Подробно изобразите рабочий процесс вложенной активности. Это называется вызываемым поведением.

    - In the called sub-activity diagram, the **Initial Node** indicates where control starts when the called behavior is invoked. The **Activity Final Node** shows where control should return to the parent activity.

4. Set the **Behavior** property of the **Call Behavior Action** to refer to the called behavior diagram.

    > [!NOTE]
    > The sub-activity diagram must have some elements on it or the diagram will not be available in the drop-down list for the **Behavior** property. Also, the trident icon will not appear on your **Call Behavior Action** shape until you set its **Behavior** property.

5. Set the **Is Synchronous** property of the action to indicate whether your activity waits for the called activity to complete.

    - If you set **Is Synchronous** to false, you are indicating that the flow can continue to the next action before the called activity finishes. Не следует определять закрепления вывода или исходящие потоки данных из действия.

### <a name="describing-data-flow-in-and-out-of-sub-activities"></a>Описание потока данных, входящих и исходящих из вложенных активностей
 Описание данных, передаваемых во вложенные действия и из них, сходно с использованием параметров в программном обеспечении.

- Создайте закрепления ввода и вывода (1) для действия поведения вызова для каждого фрагмента данных, передаваемого в активность или из нее. Назовите их.

- In the sub-activity diagram, create an **Activity Parameter Node** (2) for each input and output pin on the calling action. Присвойте каждому узлу имя, совпадающее с именем соответствующего закрепления.

  > [!NOTE]
  > Узел параметра действия похож на узел объекта. To check what type of node that you are looking at, right-click the node and then click **Properties**. Тип узла будет указан в заголовке окна "Свойства".

- На схеме вложенной активности создайте соединители, показывающие поток объектов в каждый узел параметра действия и из каждого такого узла.

  ![Pins on Call Behavior map to activity parameters](../modeling/media/uml-actguidesub.png "UML_ActGuideSub")

### <a name="Postcondition"></a> Defining Postconditions and Preconditions
 You can use the **Local Postconditions** and **Local Preconditions** properties to specify in detail the outcome of an action. Они описывают результат действия, не описывая способ достижения этого результата.

 To set these properties, right-click the action and then click **Properties**. Введите значения свойств в окне "Свойства".

#### <a name="local-postconditions"></a>Локальные постусловия
 Постусловие — это условие, которое должно быть выполнено, прежде чем действие сможет считаться завершенным. В примере действия "Подтвердить заказ" постусловием может быть, например, следующее.

 Клиент предоставил полные сведения, необходимые для обработки платежа по кредитной карте, в допустимом формате.

 Постусловие может выражать отношение между состояниями до и после выполнения действия. Пример:

 процентная ставка удвоилась.

 Можно писать постусловия в более формальном стиле, ссылаясь на определенные атрибуты данных, с которыми работают действия. Пример:

 `InvoiceTotal == Sum(OrderItem.MenuItem.Price)`

#### <a name="local-preconditions"></a>Локальные предусловия
 Предусловие — это условие, которое должно быть удовлетворено к началу действия. Например, у действия "Подтвердить заказ" может быть следующее предусловие:

 Пользователь выбрал хотя бы один элемент меню.

### <a name="describing-calls-to-operations"></a>Описание вызовов к операциям
 Как правило, действие описывает работу, выполняемую любой комбинацией людей, программ и компьютеров. Однако с помощью действия вызова операции можно описывать вызовы к определенным методам или функциям программы.

- Задайте имя действия вызова операции, указывающее, какая операция и для какого объекта или компонента вызывается.

- Добавьте к действию вызова операции закрепления ввода и вывода, чтобы описать параметры и возвращаемые значения.

- You can set the **Is Synchronous** property of the action to indicate whether your activity waits for the operation to complete.

  - If you set **Is Synchronous** to false, you are indicating that the flow can continue to the next action before the called operation is complete. Не следует определять закрепления вывода или исходящие потоки данных из действия.

## <a name="Concurrent"></a> Concurrent Flows
 You can use the **Fork Node** and the **Join Node** to describe two or more threads of activities that can execute at the same time.

 ![The fork and join nodes show concurrent flows](../modeling/media/uml-actguideconcurrent.png "UML_ActGuideConcurrent")

 The effect of the **Fork Node** (1) is to divide the thread of control into two or more threads. После завершения предыдущего действия могут запускаться все действия на выходе ветвления.

 A **Join Node** (2) brings concurrent threads together. The action after the **Join Node** may not start until all the actions leading to the **Join Node** are complete.

### <a name="describing-signals-and-events"></a>Описание сигналов и событий
 Шаг в процессе, отправляющий сигнал, можно показать как действие отправки сигнала в активности. Шаг, ожидающий конкретного сигнала или события перед продолжением работы, можно показать как действие принятия события.

 Например, можно показать шаг, отправляющий заказ, и другой шаг, который должен получить заказ, прежде чем его обработать.

#### <a name="sending-a-signal"></a>Отправка сигнала
 Действия отправки сигнала (3) позволяют указать, что какой-либо сигнал или сообщение отправлено в другие активности или процессы. Указывайте тип отправляемых сообщений в имени действия.

- Управление немедленно передается следующему действую в потоке управления (если есть).

- Действие отправки сигнала нельзя использовать для описания реакции процесса на возвращаемую информацию. Для этого нужно использовать отдельное действие приема события.

- Отобразим поток данных, входящий в действие отправки сигнала, чтобы указать, какие данные будут отправляться в исходящих сообщениях. For more information, see [Describing Data Flow](#DataFlows).

#### <a name="waiting-for-a-signal-or-event"></a>Ожидание сигнала или события
 Действия приема события (4) позволяет указать, что данное действие ожидает некоторого внешнего события или входящего сообщения. Указывайте тип ожидаемых событий в имени действия.

- Чтобы показать, что действие ожидает внешнего события или сообщения в определенной точке потока, в подходящем месте активности изобразите действие приема события с входящим потоком.

- Чтобы показать, что действие может отвечать на внешнее событие или сообщение в любое время, изобразите действие приема события без входящего потока. При возникновении указанного внешнего события в активности начнется новый поток, который начинается с действия приема события.

- Действия приема события нельзя использовать для описания значений, возвращаемых отправителю сигнала. Для этого используется отдельное действие отправки сигнала.

- Отобразив исходящие из действия потоки данных, можно продемонстрировать, каким образом активность обрабатывает данные, получаемые с сигналом. If you want to show more than one output flow, you should set the **IsUnmarshall** property of the Accept Event Action, which indicates that the action parses the incoming signal into its separate components. For more information, see [Describing Data Flow](#DataFlows).

### <a name="describing-multiple-data-flows"></a>Описание нескольких потоков данных
 Отобразив несколько потоков управления или потоков объектов, исходящих из действия, можно указать, что после завершения действия возникает несколько потоков. Это похоже на ветвление, за тем исключением, что можно использовать одновременно и потоки управления, и потоки объектов.

 В следующем примере показано несколько потоков, исходящих из действий и входящих в действия.

 ![Parallel object flows](../modeling/media/uml-actguidemulti.png "UML_ActGuideMulti")

 После завершения действия "Клиент предоставляет сведения" создаются два объекта: "Адрес поставки" и "Данные кредитной карты". Затем эти два объекта передаются на обработку различными действиями.

 Поскольку действие нуждается во всех входных данных до начала выполнения, последнее действие не начинается, пока не завершатся все ведущие к нему действия.

### <a name="streams"></a>Потоки
 С помощью схемы активности можно описывать конвейер или ряд действий, выполняющихся одновременно и постоянно передающих данные от действия к действию.

 Суть следующего примера в том, что все действия могут создавать объекты и продолжать работу. Так как здесь нет потоков управления, действия могут начинаться сразу после получения первого объекта.

 Обратите внимание, что соединители в этом примере являются потоками объектов, так как по меньшей мере один конец каждого из них находится в узле параметра действия, узле объекта или закреплении ввода или вывода.

 ![A data flow](../modeling/media/uml-actguidestream.png "UML_ActGuideStream")

 1. В данном примере есть три узла параметра действия, представляющие его вводы и выводы.

 2. Узлы объекта, закрепления ввода и закрепления вывода могут представлять буферы. Чтобы указать, сколько объектов может находиться в буфере одновременно, задайте свойство "Верхняя граница" для узла объекта.

 3. Узлы решений позволяют показать, что поток разделяется и отправляет разные объекты в различные ветви. Пояснить критерии разделения можно с помощью примечаний или заголовков узлов.

 4. Узлы ветвления позволяют показать, что создаются две или больше копий объектов, которые отправляются на параллельную обработку.

 5. Соединительные узлы позволяют показать, что два потока обработки вновь соединяются в один.

### <a name="selection-and-transformation"></a>Выбор и преобразование
 Объекты в потоке объектов могут преобразовываться, выбираться или и то и другое. Поток объектов — это поток, идущий к закреплению или узлу объекта либо в противоположном направлении.

- Преобразование описывает, каким образом объекты, входящие в поток, преобразуются в другой тип.

- Выбор описывает, каким образом только часть объектов, входящих в поток, передается принимающему действию.

  В примере показано преобразование. Первое действие на схеме 1 создает почтовый индекс на закреплении вывода. Он соединяется с закреплением ввода второго действия. При этом второе действие ожидает полный адрес. Преобразование из одного типа в другой задано во второй активности, Address Lookup (Поиск адреса). На него ссылается свойство "Преобразование" потока объектов. Активность Address Lookup содержит узел параметра действия для входящего почтового индекса и узел параметра действия для исходящего полного адреса.

  ![Object transformation defined in another diagram](../modeling/media/uml-actguidetransform.png "UML_ActGuideTransform")

  Преобразование или выбор можно задать одним из двух способов:

- Добавить комментарий к закреплению ввода или вывода.

  - To distinguish this description from a general comment, you can begin the comment with <\<**transformation**>> or <\<**selection**>>.

- Подробно описать преобразование или выбор на отдельной схеме активности.

  - При использовании этого метода также добавьте комментарий с указанием на то, что определено преобразование.

##### <a name="to-specify-a-transformation-or-selection-in-a-separate-activity-diagram"></a>Описание преобразования или выбора на отдельной схеме активности

1. Создайте новую схему активности для описания потока преобразования или выбора.

   - In **Solution Explorer**, right-click your project, point to **Add**, click **New Item**, and then click **Activity Diagram**. Присвойте схеме имя, соответствующее потоку преобразования или выделения. Нажмите кнопку **Добавить**.

2. На новой схеме выполните следующие действия.

   1. Создайте два узла параметра действия, один для входящего потока, второй для выходящего.

   2. Создайте действия, связанные с потоками объектов. Это показывает, как работает преобразование или выбор.

3. На любой схеме, где нужно использовать преобразование или выбор, выполните следующие действия.

   1. Создайте поток объектов, то есть соединитель, ведущий к закреплению ввода или вывода, узлу объекта либо узлу параметра действия или в обратном направлении.

   2. Right-click the object flow and then click **Properties**.

   3. In the **Transformation** or **Selection** property, select the diagram where you specified the transformation or selection flow.

   Можно также определить выбор для узла объекта и отдельных закреплений ввода и вывода. Define a selection activity as in the previous procedure, and then set the **Selection** property of the object node, or input or output pin.

## <a name="see-also"></a>См. также раздел
 [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md) [UML Sequence Diagrams: Reference](../modeling/uml-sequence-diagrams-reference.md) [UML Component Diagrams: Reference](../modeling/uml-component-diagrams-reference.md) [UML Use Case Diagrams: Reference](../modeling/uml-use-case-diagrams-reference.md) [UML Class Diagrams: Reference](../modeling/uml-class-diagrams-reference.md) [UML Component Diagrams: Reference](../modeling/uml-component-diagrams-reference.md) [Video: Capture Business Workflows by using Activity Diagrams](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-4-capture-business-workflows)
