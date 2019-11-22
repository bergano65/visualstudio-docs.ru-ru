---
title: 'UML Sequence Diagrams: Guidelines | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.sequencediagram.linktosequencediagram
- vs.teamarch.logicalclassdiagram.createlifeline
- vs.teamarch.componentdiagram.createlifeline
helpviewer_keywords:
- diagrams - modeling, sequence
- sequence diagrams
- UML diagrams, sequence
- interactions, UML
- diagrams - modeling, UML sequence
- UML interactions
- UML, sequence diagrams
- UML sequence diagrams
- behaviors, UML
ms.assetid: 5990ef7c-ba60-4e20-a36d-e29c1fa6c8bb
caps.latest.revision: 55
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8c5906084fc7db96ddf304e8362bf7692dac62d5
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297142"
---
# <a name="uml-sequence-diagrams-guidelines"></a>UML Sequence Diagrams: Guidelines
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio, you can draw a *sequence diagram* to show an interaction. Взаимодействие — это последовательность сообщений между типичными экземплярами классов, компонентов, подсистем или субъектов.

 Схемы последовательностей UML являются частью модели UML и существуют только в проектах моделирования UML. To create a UML sequence diagram, on the **Architecture** menu, click **New UML or Layer Diagram**. Find out more about [UML sequence diagram elements](../modeling/uml-sequence-diagrams-reference.md) or [UML modeling diagrams](../modeling/edit-uml-models-and-diagrams.md) in general. For a video demonstration, see [Sketching Interactions by using Sequence Diagrams (2010)](https://channel9.msdn.com/Blogs/clinted/UML-with-VS-2010-Part-7-Sketching-Interactions-with-Sequence-Diagrams).

 Чтобы узнать, какие версии Visual Studio поддерживают эту функцию, см. раздел [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="in-this-topic"></a>Содержание раздела
 [Using UML Sequence Diagrams](#Using)

 [Basic Steps for Drawing Sequence Diagrams](#BasicSteps)

 [Creating and Using Simple Sequence Diagrams](#Simple)

 [Classes and Lifelines](#ClassesAndLifelines)

 [Creating Reusable Interaction Sequences](#Multiple)

 [Collapsing Groups of Lifelines](#Collapse)

 [Describing Control Structures with Fragments](#Fragments)

## <a name="Using"></a> Using UML Sequence Diagrams
 Схемы последовательностей можно использовать в разных целях и на разных уровнях детализации программы. Как правило, схема последовательностей создается в указанных ниже случаях.

- Если есть схема вариантов использования, которая обобщает сведения о пользователях системы и их целях, можно создать схемы последовательностей, чтобы описать, как основные компоненты системы взаимодействуют для достижения цели каждого варианта использования. For more information, see [UML Use Case Diagrams: Guidelines](../modeling/uml-use-case-diagrams-guidelines.md).

- Если определены сообщения, поступающие в интерфейс компонента, можно создать схемы последовательностей, чтобы описать, как внутренние части компонента взаимодействуют для достижения результата, требуемого для каждого входящего сообщения. For more information, see [UML Component Diagrams: Guidelines](../modeling/uml-component-diagrams-guidelines.md).

  Создание схем последовательностей имеет несколько преимуществ.

- Можно легко увидеть, как задачи распределяются между компонентами.

- Можно определить шаблоны взаимодействия, затрудняющие обновление программы.

## <a name="relationship-to-other-diagrams"></a>Отношение к другим схемам
 Схемы последовательностей UML можно использовать с другими схемами несколькими способами.

#### <a name="lifelines-and-types"></a>Линии жизни и типы
 Линии жизни, создаваемые в схеме последовательностей, могут представлять типичные экземпляры компонентов или классов в системе. Можно создавать линии жизни из типов, а типы — из линий жизни, а также отображать типы на схемах классов и компонентов UML. For more information, see [Classes and Lifelines](#ClassesAndLifelines).

#### <a name="parameter-types"></a>Типы параметров
 С помощью схемы классов UML можно также описать типы параметров и возвращаемые значения в сообщениях, обмен которыми ведется между линиями жизни.

#### <a name="use-case-details"></a>Подробности варианта использования
 Вариант использования представляет цель пользователя, а также последовательность шагов для достижения этой цели. Последовательность шагов можно описать несколькими способами. Во-первых, можно создать схему последовательностей, показывающую взаимодействия между пользователями и основными компонентами системы. For more information, see [UML Use Case Diagrams: Guidelines](../modeling/uml-use-case-diagrams-guidelines.md).

## <a name="BasicSteps"></a> Basic Steps for Drawing Sequence Diagrams
 For a complete list of elements on sequence diagrams, see [UML Sequence Diagrams: Reference](../modeling/uml-sequence-diagrams-reference.md).

> [!NOTE]
> Detailed steps for how to create any of the modeling diagrams are described in [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md).

#### <a name="to-create-a-sequence-diagram"></a>Создание схемы последовательностей

1. On the **Architecture** menu, click **New UML or Layer Diagram**.

2. Under **Templates**, click **UML Sequence Diagram**.

3. Назовите схему.

4. In **Add to Modeling Project**, select an existing modeling project in your solution, or **Create a new modeling project**, and then click **OK**.

    A new sequence diagram appears with the **Sequence Diagram** toolbox. Эта панель содержит требуемые элементы и соединители.

   ![Parts of a sequence diagram](../modeling/media/uml-sequence.png "UML_Sequence")

#### <a name="to-draw-a-sequence-diagram"></a>Создание схемы последовательностей

1. Drag **Lifelines** (1) from the **Toolbox** onto the diagram to represent instances of classes, components, actors, or devices.

    > [!NOTE]
    > You can also create a lifeline by dragging an existing class, interface, actor or component from **UML Model Explorer** onto the diagram. Так создается линия жизни, представляющая экземпляр выбранного типа.

2. Создайте сообщения, чтобы показать, как линии жизни взаимодействуют для достижения конкретной цели.

     Чтобы создать сообщение (3, 4, 6, 7), щелкните инструмент создания сообщений. Затем щелкните отправляющую линию жизни в том месте, где необходимо начать сообщение, и щелкните получающую линию жизни.

     Вхождение выполнения (5) отображается на получающей линии жизни. Вхождение выполнения представляет период времени, в течение которого экземпляр выполняет метод. Можно создать другие сообщения, начинающиеся с вхождения выполнения.

3. Чтобы показать сообщение, поступающее из неизвестного источника события (9) или передающее данные неизвестным получателям (10), создайте асинхронное сообщение из пустого пространства на схеме или в него. These messages are called *found messages* (9) and *lost messages* (10).

    > [!NOTE]
    > To move a group of lifelines that have lost or found messages, follow these steps to select the lifelines before you move them: Draw a rectangle around those lifelines, or press and hold the **CTRL** key while you click each lifeline. If you use **Select All** or **CTRL**+**A** to select all lifelines, and then move them, any lost or found messages attached to these lifelines will not move. В этом случае такие сообщения можно переместить отдельно.

4. Создайте схемы последовательностей для каждого основного сообщения одному и тому же компоненту или системе.

#### <a name="to-change-the-order-of-messages"></a>Изменение порядка сообщений

- Перетащите сообщение вверх или вниз по соответствующей линии жизни. Вы можете перетаскивать сообщения на другие сообщения, а также в блок выполнения или из него.

     \- или -

- Click the message and use the **UP ARROW** and **DOWN ARROW** keys to adjust message positions. Use **SHIFT+UP ARROW** and **SHIFT+DOWN ARROW** to change the order of the messages.

#### <a name="to-move-or-copy-message-sequences-on-the-sequence-diagram"></a>Перемещение или копирование последовательностей сообщений на схеме последовательностей

1. Right-click a message (3, 4) and then click **Copy**.

2. Right-click the execution occurrence (5) or a lifeline (1) from which you want the new message to be sent, and then click **Paste**. При необходимости нового отправителя можно изобразить на другой схеме.

     Копия сообщения и все его дочерние сообщения добавляются в конец вхождения выполнения или в конец линии жизни.

    > [!NOTE]
    > Вставленное сообщение всегда отображается в конце вхождения выполнения или линии жизни. Вставив сообщение, можно перетащить его на прежнее место.

#### <a name="to-display-and-edit-the-signature-text-for-a-message"></a>Отображение и изменение текста подписи сообщения

- Для того чтобы текст подписи был видим, линия жизни целевого объекта должна быть связана или сопоставлена с каким-либо типом. Для выполнения этой задачи необходимо выполнить одно из указанных ниже действий.

  - Right-click the lifeline, and then choose **Create Class**.

     \- или -

  - Select the lifeline, press **F4**, and then in the **Properties** window, set the **Type** property to an existing type or specify the name for a new type. Right-click the message label, and then choose **Create Operation**.

    Текст подписи отобразится под меткой сообщения. Теперь текст подписи можно изменять. For more information, see [Classes and Lifelines](#ClassesAndLifelines).

#### <a name="to-improve-the-layout-of-a-sequence-diagram"></a>Оптимизация размещения элементов на схеме последовательностей

- Right-click a blank part of the diagram, and then click **Rearrange Layout**.

- To undo the operation, click **Edit**, and then click **Undo**.

#### <a name="to-change-the-package-that-owns-the-interaction"></a>Изменение пакета, которому принадлежит взаимодействие

1. In **UML Model Explorer**, find the Interaction that the sequence diagram displays.

    > [!NOTE]
    > The interaction will not appear in **UML Model Explorer** until you add the first lifeline to the sequence diagram.

2. Перетащите взаимодействие в пакет.

     \- или -

     Right-click the Interaction, and then click **Cut**. Right-click the Package, and then click **Paste**.

## <a name="Simple"></a> Creating and Using Simple Sequence Diagrams
 Наиболее простая и часто используемая форма схемы последовательностей содержит только линии жизни и сообщения. Схема этого вида позволяет ясно показать типичную последовательность взаимодействий между объектами в проектируемой системе или между системой и ее пользователями. Часто этого достаточно, чтобы обсуждать проектируемую систему и передавать сведения о ней.

 При создании простой схемы последовательностей не следует забывать об указанных ниже моментах.

### <a name="types-of-message"></a>Типы сообщений
 Для создания сообщений можно использовать три различных инструмента.

- Use the **Synchronous** tool to describe an interaction in which the sender waits for the receiver to return a response (3).

     A **<\<return>>** arrow will be shown at the end of the execution occurrence. Она обозначает, что контроль над взаимодействием возвращается отправителю.

- Use the **Asynchronous** tool to describe an interaction in which the sender can continue immediately without waiting for the receiver (4).

- Use the **Create** tool to describe an interaction in which the sender creates the receiver (8).

     Сообщение о создании должно быть первым сообщением, которое получит получатель.

### <a name="annotating-the-interactions"></a>Создание заметок о взаимодействиях
 To describe more detail about the sequence, you can place a **Comment** anywhere on the diagram.

 Using **Comment Links**, you can link a comment to lifelines, executions, interaction uses, and fragments.

> [!CAUTION]
> Если нужно прикрепить комментарий к определенной точке последовательности, свяжите его с вхождением выполнения, использованием взаимодействия или фрагментом. Не связывайте комментарий с линией жизни, потому что в этом случае он не будет прикреплен к правильной точке последовательности.

 Используйте комментарий в указанных ниже целях.

- Чтобы отметить, что было достигнуто в ключевых точках последовательности. Это позволяет другим пользователям видеть цели взаимодействий.

- Чтобы описать общую цель всей последовательности. Прикрепить комментарий к начальному вхождению выполнения или не прикреплять его ни к чему. Пример: "Клиент выбрал пункты из меню, и ему была предоставлена информация о стоимости этих пунктов".

- Чтобы описать обязанности каждой линии жизни. Прикрепите комментарий к линии жизни. Пример: "Менеджер по обработке заказов собирает сведения о выбранных клиентом пунктах меню".

- Чтобы создавать примечания об исключениях и других вариантах последовательностей, которые могут быть выполнены в качестве альтернативы показанной типичной последовательности. Пример: "Клиент может пропустить остальные элементы последовательности".

  - В качестве более формальной альтернативы этого вида примечаний можно использовать фрагменты. See [Describing Control Structures with Fragments](#Fragments)

## <a name="deciding-the-scope-of-the-diagram"></a>Определение области действия схемы
 Очень важно четко обозначить, что должно отображаться на схеме.

#### <a name="initiating-event"></a>Инициирующее событие
 На каждой схеме должна быть показана последовательность взаимодействий, порождаемых одним инициирующим событием. Это может быть, например, одно из следующих событий:

- инициация варианта использования пользователем (например, открытие веб-страницы для покупки продуктов питания);

- сообщение от одного системного компонента другому, например с запросом о доступности пунктов, которые желает приобрести клиент;

- событие, инициируемое изменением состояния, например если уровень запасов определенного товара падает ниже порогового значения.

#### <a name="level-of-detail"></a>Уровень детализации
 Схемы последовательностей могут иметь разные уровни детализации. Уровень детализации можно определять в двух разных измерениях практически независимо друг от друга.

 Линии жизни могут представлять один из следующих уровней детализации:

- объекты в существующем или разрабатываемом программном коде;

- компоненты или их подкомпоненты, как правило, без видов, посредников и других соединительных механизмов;

- система и внешние субъекты.

  Сообщения могут представлять один из следующих уровней детализации:

- программные сообщения в программном коде, в API или веб-интерфейсе;

- транзакции или подтранзакции, например между пользователями и системой или между кодом и базой данных;

- варианты использования — основные взаимодействия между пользователями и системой.

  При анализе существующего кода или описании новой проектируемой системы часто имеет смысл создавать и анализировать представления с меньшей детализацией.

## <a name="describing-variations"></a>Описание вариантов
 На схеме отображается одна типичная последовательность событий. Если нужно показать альтернативные возможности, такие как сценарии сбоев, можно воспользоваться одним из следующих методов:

- создать отдельные схемы последовательностей для описания этих сценариев;

- Use [Describing Control Structures with Fragments](#Fragments) to show loops, alternatives, and so on.

## <a name="assessing-the-design"></a>Оценка проекта
 Схему можно использовать для оценки распределения задач между ее объектами или компонентами. Необходимо провести реструктуризацию, если наблюдаются указанные ниже явления.

- Создается впечатление, что одна линия жизни выполняет все функции, вызывая все остальные элементы схемы, в то время как другие линии жизни лишь пассивно отвечают на эти вызовы.

- Многие сообщения пересекают линии жизни. Каждая линия жизни должна отправлять сообщения небольшому числу соседних элементов и не должна взаимодействовать с их соседями. Как правило, имеется возможность расположить линии жизни так, чтобы сообщения пересекали линии жизни всего в нескольких местах. В местах пересечения целевая линия жизни не должна обмениваться сообщениями, пересекающими какие-либо другие линии жизни.

- Некоторые линии жизни выполняют несколько разных видов задач. Область ответственности каждой линии жизни должна описываться в одном кратком предложении. В нем должны обобщаться сведения о том, что линия жизни делает в ответ на каждое получаемое сообщение.

## <a name="ClassesAndLifelines"></a> Classes and Lifelines
 Линии жизни на схемах последовательностей показывают экземпляры классов или интерфейсов компонентов. Существует два способа именования линии жизни.

|**For this purpose**|**Use this format**|
|--------------------------|-------------------------|
|Анонимный экземпляр типа.<br /><br /> Используйте его, если для каждого типа имеется только одна линия жизни.|*typeName*|
|Именованный экземпляр типа.<br /><br /> Используйте его, если необходимо показать последовательность, включающую несколько экземпляров одного типа.|*objectName*:*typeName*|

### <a name="creating-lifelines-from-types"></a>Создание линий жизни на основе типов
 Линии жизни можно создавать из уже определенных классов (например, на схеме классов).

> [!NOTE]
> Прежде чем выполнять эту задачу, убедитесь в том, что имеется схема последовательностей.

##### <a name="to-create-a-lifeline-from-an-existing-type"></a>Создание линии жизни на основе существующего типа

- Перетащите класс, компонент или интерфейс из обозревателя моделей UML на схему последовательностей.

   \- или -

  1. Right-click the class, component, or interface on its respective diagram, and then click **Create Lifeline**.

  2. In the **Create Lifeline** dialog box, select a sequence diagram, and then click **OK**.

     Появится новая линия жизни с именованным экземпляром. Ее типом является тип, который вы перетащили.

  > [!NOTE]
  > Это действие можно повторять неограниченное число раз. При этом создаются линии жизни с разными именами экземпляров.

##### <a name="to-change-the-type-of-a-lifeline"></a>Изменение типа линии жизни

1. Right-click a lifeline, and then click **Properties**.

2. In the **Properties** window, set the **Type** property. Можно выбрать тип из раскрывающегося меню или указать новое имя.

### <a name="creating-classes-from-lifelines"></a>Создание классов на основе линий жизни
 Создав одну или несколько схем последовательностей, можно обобщить линии жизни, создав на их основе классы или интерфейсы.

##### <a name="to-create-a-class-or-interface-from-a-lifeline"></a>Создание класса или интерфейса на основе линии жизни

1. Right-click the lifeline, and then click **Create Class** or **Create Interface**.

     В обозревателе моделей UML появится новый класс или интерфейс.

2. Создайте в классе или интерфейсе операции для каждого получаемого линией жизни сообщения.

    1. Выделите все сообщения, которые нужно включить.

    2. Right-click one of the messages, and then click **Create Method**.

         Новый класс или интерфейс имеет операции для каждого выделенного сообщения.

         The operation name appears below each message arrow, and in the **Operation** property of the message.

         Если сообщение включает параметры в форме "(параметр : тип)", они отобразятся в списке параметров новой операции.

        > [!NOTE]
        > Если в схему последовательностей добавляются новые сообщения, этот шаг необходимо повторить.

3. Чтобы просмотреть подробные сведения о новом классе или интерфейсе, добавьте его в схему классов или компонентов.

    1. Откройте или создайте схему классов или компонентов.

    2. Drag the new class or interface from **UML Model Explorer** to a class diagram.

         Класс или интерфейс появится на схеме классов.

         \- или -

    3. Drag the new interface from **UML Model Explorer** onto a component or port in a component diagram.

         Интерфейс отображается в компоненте в качестве обозначения без описания операций.

### <a name="creating-classes-for-parameters"></a>Создание классов параметров
 В сообщения на схеме последовательностей можно включить параметры. Схему классов UML можно использовать для описания типов параметров.

## <a name="Multiple"></a> Creating Reusable Interaction Sequences
 Для описания последовательности можно использовать отдельную схему, которая содержит подробные сведения, которые необходимо отделить от других, либо сведения, относящиеся к нескольким схемам.

 На одной схеме можно создать прямоугольник использования взаимодействия (12), указывающий на подробные сведения на другой схеме.

 Дважды щелкните использование взаимодействия, чтобы открыть связанную с ним схему последовательностей.

#### <a name="to-create-a-reusable-interaction-sequence-from-existing-lifelines"></a>Создание последовательности взаимодействий с возможностью повторного использования на основе существующих линий жизни

1. In the **Toolbox**, click **Interaction Use**.

2. Удерживая нажатой кнопку мыши, перетащите по схеме последовательностей линии жизни, которые нужно включить в последовательность с возможностью повторного использования. Начните с выбора положения по вертикали для вставки использования взаимодействия.

     Использование взаимодействия отображается напротив выбранных линий жизни на схеме последовательностей.

3. Дважды щелкните имя использования взаимодействия и переименуйте его, чтобы описать результат последовательности с возможностью повторного использования на этой схеме.

     \- или -

     Напишите имя в качестве вызова функции с параметрами.

4. Свяжите использование взаимодействия с другой схемой последовательностей. Щелкните использование взаимодействия правой кнопкой мыши и выполните одно из указанных ниже действий.

     Click **Create New Sequence** to create a new sequence diagram

     \- или -

     Click **Link to Sequence** to link to an existing diagram.

     Visual Studio создает связь между использованием взаимодействия и новой последовательностью взаимодействий.

     В решении появляется новая схема последовательностей. На ней отображаются линии жизни, с помощью которых было создано использование взаимодействия.

    > [!NOTE]
    > Отображаются только те линии жизни, с помощью которых было создано использование взаимодействия. На новой схеме не будут отображаться линии жизни, созданные после использования взаимодействия, даже если использование взаимодействия включает эти линии.

#### <a name="to-create-a-reusable-sequence-from-existing-messages"></a>Создание последовательности с возможностью повторного использования на основе существующих сообщений

- Right-click the message that you want to move, and then click **Move to Diagram**.

  Visual Studio:

  - заменяет выделенное сообщение и любые дочерние сообщения использованием взаимодействия;

  - перемещает замещенные сообщения на новую схему последовательностей;

  - создает связь между использованием взаимодействия и новой схемой последовательностей.

#### <a name="to-navigate-to-the-sequence-referenced-by-an-interaction-use"></a>Переход к последовательности, на которую ссылается использование взаимодействия

- Дважды щелкните использование взаимодействия.

     \- или -

     Right-click the interaction use and then click **Go to Sequence**.

### <a name="creating-a-placeholder-with-an-interaction-use"></a>Создание заполнителя с использованием взаимодействия
 Вы можете создать использование взаимодействия, не связывая его с другой схемой. You can use this as a placeholder for a part of the sequence whose details are yet to be worked out. Use the name of the interaction use to indicate the outcome that you want.

## <a name="Collapse"></a> Collapsing Groups of Lifelines
 Вы можете свернуть несколько линий жизни, чтобы группа отображалась как одна линия. Так можно визуально представить группу объектов как один компонент. Сообщения и использования взаимодействий между линиями жизни свернутой группы скрыты. Сообщения и последовательности взаимодействий, включающие другие линии жизни, отображаются.

#### <a name="to-collapse-a-group-of-lifelines-together"></a>Сворачивание группы линий жизни

1. Выберите две или более линий жизни.

2. Right-click one of them, and then click **Collapse**.

     Несколько линий жизни заменяются одной.

     Сообщения и использования взаимодействия, включающие только члены этой группы, скрыты.

3. Щелкните имя, чтобы переименовать группу.

    > [!NOTE]
    > Если развернуть группу, ее имя будет утеряно.

#### <a name="to-expand-a-collapsed-group"></a>Разворачивание свернутой группы

- Right-click the collapsed lifeline, and then click **Expand**.

    > [!NOTE]
    > Имя группы будет утеряно, равно как и любые ссылки из группы на комментарии или рабочие элементы.

## <a name="Fragments"></a> Describing Control Structures with Fragments
 Для определения циклов, ветвей и параллельной обработки на схеме последовательностей можно использовать объединенные фрагменты (13). Эти сведения можно отобразить и на схеме деятельности. Схема деятельности не позволяет показывать сообщения, которыми обмениваются субъекты, так же наглядно, но иногда с ее помощью можно более эффективно представить циклы, ветви и параллелизм.

 For a full list of the types of fragment, see [Describe control flow with fragments on UML sequence diagrams](../modeling/describe-control-flow-with-fragments-on-uml-sequence-diagrams.md).

#### <a name="to-create-a-combined-fragment"></a>Создание объединенного фрагмента

1. Выделите сообщение или последовательность сообщений, начинающихся в одном вхождении выполнения или на одной линии жизни.

    > [!NOTE]
    > Выделите стрелки сообщений, а не вхождения выполнения, на которые указывают сообщения.

2. Right-click one of the messages, point to **Surround With**, and then click the type of fragment that you require.

     Появится новый фрагмент. В нем содержатся выбранные сообщения.

     Если тип объединенного фрагмента допускает наличие нескольких фрагментов, отображается также пустой фрагмент.

3. To set the guard of a fragment, right-click the fragment border, and then click **Properties**. Set the **Guard** property.

     Условие используется для определения требований к ветви или циклу.

4. To add a new fragment to a kind that allows multiple fragments, right-click the boundary of a fragment, and point to **Add**. Click either **Interaction Operand Before** or **Interaction Operand After**.

5. Чтобы добавить во фрагмент новые сообщения, используйте инструменты создания сообщений либо скопируйте и вставьте их во фрагмент.

## <a name="see-also"></a>См. также раздел
 [UML Sequence Diagrams: Reference](../modeling/uml-sequence-diagrams-reference.md) [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md) [UML Use Case Diagrams: Reference](../modeling/uml-use-case-diagrams-reference.md) [UML Class Diagrams: Reference](../modeling/uml-class-diagrams-reference.md) [UML Component Diagrams: Reference](../modeling/uml-component-diagrams-reference.md) [UML Component Diagrams: Reference](../modeling/uml-component-diagrams-reference.md) [Video: Sketching Interactions by using Sequence Diagrams](https://go.microsoft.com/fwlink/?LinkId=201113)
