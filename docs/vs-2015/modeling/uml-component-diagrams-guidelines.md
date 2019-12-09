---
title: 'UML Component Diagrams: Guidelines | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML diagrams, component
- diagrams - modeling, component
- diagrams - modeling, UML component
- UML, component diagrams
- component diagrams
ms.assetid: 6c1bdd60-369e-477e-83ed-7f6fe75c9f0b
caps.latest.revision: 37
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 99f2b67d264edcaab5272d0224d4450ee2e8a6f6
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297160"
---
# <a name="uml-component-diagrams-guidelines"></a>UML-схемы компонентов: правила работы
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio, you can draw a *component diagram* to show the structure a software system. For a video demonstration, see [Designing the Physical Structure by using Component Diagrams](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-6-designing-a-projects-physical-structure).

 Чтобы узнать, какие версии Visual Studio поддерживают эту функцию, см. раздел [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 To create a UML component diagram, on the **Architecture** menu, click **New UML or Layer Diagram**.

 Компонент — это модульная единица, заменяемая в пределах среды. Its internals are hidden, but it has one or more well-defined *provided interfaces* through which its functions can be accessed. A component can also have *required interfaces*. Требуемый интерфейс определяет, какие функции и службы он требует от других компонентов. Объединив предоставленные и требуемые интерфейсы нескольких компонентов, можно создать более крупный компонент. Можно сказать, что вся программная система, по сути, представляет собой компонент.

 Создание схем компонентов имеет несколько преимуществ.

- Анализ основных элементов системы позволяет команде разработчиков понять принципы существующей системы и создать новую.

- Представление системы в качестве коллекции компонентов с четко определенными предоставленными и требуемыми интерфейсами позволяет более эффективно разделить компоненты. В свою очередь, это облегчает понимание конструкции системы и ее корректирование при изменении требований.

  Можно использовать схему компонентов, чтобы представить конструкцию системы независимо от того, какой язык или платформа используется сейчас или будет использоваться в будущем.

## <a name="OtherDiagrams"></a> Relationship to Other Diagrams
 Можно использовать схему компонентов совместно с другими схемами.

|Другая схема|Помогает обсуждать следующие аспекты конструкции и передавать сведения о них|
|-------------------|--------------------------------------------------------------------|
|Схема последовательностей UML|-   Interactions between a system's components<br />-   Interactions and between the parts inside a component.<br /><br /> For more information, see [UML Sequence Diagrams: Guidelines](../modeling/uml-sequence-diagrams-guidelines.md).|
|UML-схема классов|-   The interfaces of a component. Схема классов позволяет детализировать методы интерфейса.<br />-   The data sent in parameters across the components' interfaces.<br /><br /> For more information, see [UML Class Diagrams: Guidelines](../modeling/uml-class-diagrams-guidelines.md).|
|Схемы активности|-   The internal processing performed by a component in response to incoming messages.<br /><br /> For more information, see [UML Activity Diagrams: Guidelines](../modeling/uml-activity-diagrams-guidelines.md).|
|Схемы слоев|-   Logical architectural tiers for your components.<br /><br /> For more information, see [Layer Diagrams: Reference](../modeling/layer-diagrams-reference.md).|

## <a name="Basics"></a> Basic Steps for Drawing Component Diagrams
 For reference information about the elements on component diagrams, see [UML Component Diagrams: Reference](../modeling/uml-component-diagrams-reference.md).

 For more information about how to use component diagrams in the process of design, see [Model your app's architecture](../modeling/model-your-app-s-architecture.md).

> [!NOTE]
> Detailed steps for creating any of the modeling diagrams are described in [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md).

#### <a name="to-create-a-component-diagram"></a>Создание схемы компонентов

1. On the **Architecture** menu, click **New UML or Layer Diagram**.

2. Under **Templates**, click **UML Component Diagram**.

3. Назовите схему.

4. In **Add to Modeling Project**, select an existing modeling project in your solution, or **Create a New Modeling Project**, and then click **OK**..

     A new component diagram appears with the UML **Component Diagram** toolbox. Панель элементов содержит требуемые элементы и отношения.

### <a name="drawing-components"></a>Создание компонентов
 ![Components with interfaces](../modeling/media/uml-compdrawing.png "UML_CompDrawing")

 Create a *component* (1) for each major functional unit in your system or application.

 В качестве примеров можно привести приложение, аппаратное средство, веб-службу, сборку .NET, программный класс или группу классов или любой другой отделимый сегмент программы.

##### <a name="to-create-components"></a>Создание компонентов

1. Click **Component** in the toolbox, and then click a blank part of the diagram.

     \- или -

     Скопируйте и вставьте существующий компонент.

    1. Find an existing component in a diagram or in **UML Model Explorer**.

    2. Right-click the component and then click **Copy**.

    3. Откройте схему, на которой необходимо отобразить скопированный компонент.

    4. Right-click a blank part of the diagram and then click **Paste**.

         Копия компонента отображается с новым именем.

2. Щелкните имя компонента, чтобы изменить его.

3. Щелкните шеврон (5), если нужно отобразить только заголовок компонента.

### <a name="showing-the-ports-of-a-component"></a>Отображение портов компонента
 A *port* (2, 3) represents a group of messages or operation calls that pass either into or out of a component. Группа описывается интерфейсом, который определяет тип порта. Порт может либо предоставлять, либо требовать интерфейс.

 A port with a *provided interface* (2) supplies operations that are implemented by the component, and that can be used by other components.

 В качестве примеров можно назвать пользовательский интерфейс, веб-службу, интерфейс .NET или коллекцию функций на любом языке программирования.

 A port with a *required interface* (3) represents a component's requirement for a group of operations or services to be provided by other components or external systems.

 Например, веб-браузер требует веб-серверы, а надстройка приложения требует службы из приложения.

 Компонент может иметь неограниченное число портов.

##### <a name="to-add-ports-to-a-component"></a>Добавление портов в компонент

1. In the toolbox, click **Provided Interface** or **Required Interface**.

2. Щелкните компонент, который необходимо добавить в интерфейс.

    На границе компонента появляется порт.

    Новый интерфейс создается как тип порта. This interface appears in **UML Model Explorer**.

3. Перетащите порт через границу компонента и разместите его, где нужно.

4. Перетащите метку порта, чтобы скорректировать его расположение.

5. Щелкните метку, чтобы изменить ее. Метка показывает имя интерфейса. Если изменить ее, изменится и имя интерфейса.

   Если необходимо указать атрибуты и операции интерфейса, это можно сделать, добавив их в интерфейс в обозревателе моделей UML. Кроме того, можно перетащить интерфейс из обозревателя моделей UML на схему классов и добавить операции и атрибуты на ней.

### <a name="linking-between-components"></a>Ссылки между компонентами
 Используйте зависимость (4), чтобы показать, что требования одного компонента можно удовлетворить операциями или службами, предоставленными другим компонентом.

##### <a name="to-show-that-a-provided-interface-can-satisfy-a-required-interface"></a>Как показать, что предоставленный интерфейс может удовлетворить условия требуемого интерфейса

1. In the toolbox, click **Dependency**.

2. Щелкните порт с требуемым интерфейсом одного компонента, затем щелкните порт с предоставленным интерфейсом другого компонента.

   Следует избегать создания циклов зависимости, в которых каждый компонент группы зависит от всех остальных компонентов.

##### <a name="to-add-a-port-for-an-existing-interface-to-a-component"></a>Добавление в компонент порта для существующего интерфейса

- Find the interface in **UML Model Explorer** and then drag it from there onto the component.

     \- или -

- Скопируйте и вставьте ссылку на интерфейс из схемы.

    1. On a class diagram or a component diagram, right-click the interface and then click **Copy**.

    2. On the component diagram, right-click the component, and then click **Paste Reference**.

         В компоненте отобразится предоставленный интерфейс. Рядом отобразится тег действия.

        > [!NOTE]
        > If you use **Paste** instead of **Paste Reference**, a new interface that has a new name will be created.

    3. If you wanted to create a required interface, click the Action tag and then click **Convert to Required Interface**.

## <a name="Parts"></a> Showing the Internal Parts of a Component
 ![Component diagram showing internal parts](../modeling/media/uml-compshowing.png "UML_CompShowing")

 Можно разместить части (3) в компоненте (1), чтобы показать, что он состоит из более мелких компонентов, взаимодействующих друг с другом.

 Схема на иллюстрации показывает, что каждый экземпляр веб-службы Dinner Now содержит один экземпляр сервера "Клиенты" и один экземпляр сервера "Кухня".

 Часть — это свойство родительского компонента. Отношения между ними можно сравнить с тем, как атрибут принадлежит к обычному классу. Часть имеет собственный тип, который, как правило, также является компонентом. Метка части имеет ту же форму, что и обычный атрибут.

 `+ partName : TypeName`

 Внутри родительского компонента каждая часть показывает предоставляемые и требуемые интерфейсы, определенные для ее типа (4, 5). Операции или службы, требуемые одной частью, могут быть предоставлены другой. You can use **Part Assembly** connectors to show how parts are connected with one another (6).

 Также можно показать, что одна из частей родительского компонента фактически предоставляет или требует его интерфейс. You can connect a port of the parent to a port of an internal part using a **Delegation** relation (9). Оба порта должны относиться к одному виду (предоставленные или требуемые) и иметь совместимые типы интерфейса.

 Новую часть можно создать либо с помощью нового типа, либо из существующего типа.

#### <a name="to-add-parts-to-a-component"></a>Добавление частей в компонент

1. Создайте часть для каждой крупной функциональной единицы, которая является частью родительского компонента.

    1. Click **Component** in the toolbox, and then click inside the parent component (1).

         Новая часть (3) появляется внутри родительского компонента.

         A new component is created in **UML Model Explorer**. Это тип новой части.

         \- или -

         Перетащите существующий компонент из Проводника по моделям UML в родительский компонент.

         Новая часть (3) появляется внутри родительского компонента. Ее тип — это компонент, перемещенный из Проводника по моделям UML.

         \- или -

         Right-click a component, either in a diagram or in UML Model Explorer, and then click **Copy**.

         Right-click on the parent component, and then click **Paste Reference**.

         Новая часть (3) появляется внутри родительского компонента. Ее тип — это скопированный компонент.

    2. Щелкните имя новой части, чтобы изменить его. Изменить ее тип невозможно.

    3. В новую часть можно добавить предоставленные и требуемые интерфейсы (4, 5). Click the **Provided Interface** or **Required Interface** tool, and then click in the part.

         \- или -

         Drag an existing interface from **UML Model Explorer** onto the part.

         Интерфейсы добавляются в тип части и отображаются в самой части. При необходимости корректируется размер родительского компонента.

2. Соедините части друг с другом.

    - Use the **Dependency** tool to connect the ports of different parts (6).

3. Соедините части с портами родительского компонента.

    1. Создайте один или несколько портов (7) в родительском компоненте. Click **Required Interface** or **Provided Interface** on the toolbox, and then click the parent component.

    2. Делегируйте (9) порт одной или нескольким частям. Click the **Delegation** tool, then a port on the parent component, and then a port on a part. Можно соединить порты, предоставляющие или требующие интерфейсы аналогичным способом.

### <a name="showing-the-parts-of-a-part"></a>Отображение частей части
 После разложения компонента на части каждый тип части можно дополнительно разложить на внутренние части.

 Удобнее разместить каждый слой разложения на отдельной схеме компонентов. Сначала нужно найти тип части. Например, на иллюстрации одна из частей называется `DNCustomerServer`, а ее тип представляет собой компонент, который называется `CustomerServer`. Этот тип можно найти в Проводнике по моделям UML и поместить его на другую схему. Затем можно создавать внутренние части типа.

##### <a name="to-place-a-parts-type-on-a-diagram"></a>Размещение типа части на схеме

1. Определите полное имя для типа части.

     Right-click the part and then click **Properties**.

     The type name appears in the **Type** field of the Properties window.

2. Locate the part's type in **UML Model Explorer**.

     Click **View**, point to **Other Windows**, and then click **UML Model Explorer**.

     Разверните проект и (при необходимости) любой пакет, к которому принадлежит тип.

     The type will be listed as a **Component**.

     При необходимости его имя можно изменить здесь.

3. Откройте или создайте другую схему компонентов.

4. Перетащите тип из Проводника по моделям UML на схему.

     Представление типа отображается как компонент на схеме.

     Он имеет те же интерфейсы, которые были определены для части.

     Теперь можно добавлять части в компонент.

## <a name="Designing"></a> Designing the Component

### <a name="describing-how-the-parts-collaborate"></a>Описание взаимодействия частей
 Можно создать схему последовательностей, чтобы показать, как части взаимодействуют друг с другом в ответ на сообщение, поступающее в родительский компонент.

 Можно использовать эти схемы, чтобы проанализировать существующий компонент и создать новый.

 При конструировании компонента можно создавать схемы последовательностей, даже если еще не решено, какие части будут входить в его состав. Схемы последовательностей можно использовать, чтобы поэкспериментировать с различными частями, требуемыми интерфейсами и последовательностями сообщений. Создайте схемы последовательностей для наиболее часто встречающихся и наиболее важных входящих сообщений. После этого можно создавать части в компоненте, которые соответствуют выбранным линиям жизни.

 Используйте схемы последовательностей, чтобы оценить, как функционирование системы распределяется между разными компонентами.

- Если слишком много функций делегировано одной части, вероятно, возникнут сложности с обновлением приложения. При равномерном распределении функций это маловероятно.

- Если функции, напротив, распределены между большим числом компонентов, между которыми существует много взаимодействий, производительность системы может снизиться, ее понимание будет затруднено.

  ![Sequence diagram showing collaborating parts](../modeling/media/uml-compdescparts.png "UML_CompDescParts")

##### <a name="to-draw-a-sequence-diagram-that-shows-collaboration-between-parts"></a>Создание схемы последовательностей, показывающей взаимодействие частей

1. Создайте новую схему последовательностей.

     For more information, see [UML Sequence Diagrams: Guidelines](../modeling/uml-sequence-diagrams-guidelines.md).

2. Создайте линию жизни для внешнего компонента, пользователя, устройства или другого субъекта (1), отправляющего сообщения этому компоненту.

     You can set the **Actor** property of this lifeline to true, to indicate that it is external to the component under consideration. Над линией жизни отображается контурограмма.

3. Создайте линию жизни для предоставленного интерфейса (2) этого компонента, которому выбранный субъект отправляет сообщения.

4. Создайте линию жизни для каждой части (3) компонента.

5. Создайте линию жизни для каждого требуемого интерфейса (4) компонента.

6. Создайте сообщения от внешнего субъекта (5). Покажите, как сообщение передается частям и как они взаимодействуют в ответ на него.

7. При необходимости покажите сообщения, отправляемые требуемому интерфейсу (6). Не показывайте никаких подробностей в области выполнения сообщения.

### <a name="is-the-component-more-than-its-parts"></a>Компонент — это больше, чем его части?
 В некоторых случаях компонент — это не больше, чем имя, присвоенное коллекции частей. Всю работу выполняют части, и во время выполнения нет ни кода, ни других артефактов, которые представляют компонент.

 You can indicate this in the model by setting the **Is Indirectly Instantiated** property of the component. В этом случае все интерфейсы компонента должны находиться в портах и иметь делегирования во внутренние части.

### <a name="describing-the-process-inside-each-part"></a>Описание процесса внутри каждой части
 Чтобы показать, как компонент обрабатывает каждое входящее сообщение, можно использовать схемы активности. For more information, see [UML Activity Diagrams: Guidelines](../modeling/uml-activity-diagrams-guidelines.md).

 ![Activity diagram with data buffer](../modeling/media/uml-compdescribingproc.png "UML_CompDescribingProc")

 Используйте "Принять действие события" (1), чтобы показать, что входящее сообщение начинает новый поток.

 Используйте узлы объекта и закрепления ввода или вывода, чтобы показать поток сведений и показать, где хранятся сведения. В этом примере узел объекта (2) показывает элементы, буферизованные между двумя потоками.

### <a name="defining-data-and-classes"></a>Определение данных и классов
 UML-схему классов можно использовать, чтобы подробно описать содержимое следующих элементов:

- интерфейсов компонентов; При добавлении порта, который требует или предоставляет интерфейсы компоненту, интерфейс отображается в обозревателе моделей UML. Можно перетащить или скопировать его на схему классов UML, чтобы отобразить его атрибуты и операции, а также отношения с другими интерфейсами.

- данных, переданных в параметрах операций в интерфейсах;

- данных, сохраненных в компонентах, например как показано в потоках объектов на схемах активности;

### <a name="general-dependencies-between-components"></a>общих зависимостей между компонентами.
 Можно использовать схему компонентов только для того, чтобы показать основные части конструкции и взаимозависимости между ними.

 ![A dependency between components](../modeling/media/uml-compdepend.png "UML_CompDepend")

 Use the **Dependency** tool to draw a dependency. Это означает, что конструкция одного компонента зависит от конструкции другого.

 Наиболее распространены следующие виды зависимостей.

- Один компонент вызывает код внутри другого.

- Один компонент создает экземпляр класса, определенного внутри другого класса.

- Один компонент использует сведения, созданные другим.

  Можно использовать имя стрелки зависимости, чтобы обозначить конкретный вид использования. To set the name, right-click the arrow, then click **Properties**, and set the **Name** field in the properties window.

## <a name="see-also"></a>См. также раздел
 [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md) [UML Component Diagrams: Reference](../modeling/uml-component-diagrams-reference.md) [UML Sequence Diagrams: Reference](../modeling/uml-sequence-diagrams-reference.md) [UML Use Case Diagrams: Reference](../modeling/uml-use-case-diagrams-reference.md) [UML Class Diagrams: Reference](../modeling/uml-class-diagrams-reference.md) [UML Component Diagrams: Reference](../modeling/uml-component-diagrams-reference.md) [Video: Designing the Physical Structure by using Component Diagrams](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-6-designing-a-projects-physical-structure)
