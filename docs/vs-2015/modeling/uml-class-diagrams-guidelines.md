---
title: 'UML Class Diagrams: Guidelines | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.logicalclassdiagram.overrideoperationsdialog
helpviewer_keywords:
- UML diagrams, class
- diagrams - modeling, class
- UML, class diagrams
- class diagrams - UML
- diagrams - modeling, UML class
ms.assetid: 94dbfd55-b300-4b49-9049-0831ed849486
caps.latest.revision: 56
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c170827825d772f4d97cd22f0b5754232e8d2257
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297289"
---
# <a name="uml-class-diagrams-guidelines"></a>UML-схемы классов: правила работы
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio, you can use a *UML class diagram* to describe data types and their relationships separately from their implementation. Схема позволяет сконцентрироваться на логических аспектах классов, а не их реализации.

 To create a UML class diagram, on the **Architecture** menu, choose **New UML Diagram or Layer Diagram**.

 Чтобы узнать, какие версии Visual Studio поддерживают эту функцию, см. раздел [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!NOTE]
> Этот раздел посвящен UML-схемам классов. Существует другой вид схемы классов, которую можно создать и использовать для визуализации программного кода. See [Designing and Viewing Classes and Types](https://go.microsoft.com/fwlink/?LinkId=142231).

## <a name="Using"></a> Using UML Class Diagrams
 UML-схему классов можно использовать в разных целях.

- Для предоставления описания типов, используемых в системе и передаваемых между компонентами, независимо от реализации.

     Например, тип "Заказ еды" может реализовываться в бизнес-слое в коде .NET, в интерфейсах между компонентами в XML, в базе данных в SQL и в пользовательском интерфейсе в HTML. Несмотря на то что подробности этих реализаций различаются, отношение между типом "Заказ еды" и другими типами, такими как "Меню" и "Оплата", сохраняется. UML-схема классов позволяет обсуждать эти отношения отдельно от реализаций.

- Для более точного определения набора терминов, используемых для обмена сведениями между приложением и его пользователями, а также в описаниях потребностей пользователей. See [Model user requirements](../modeling/model-user-requirements.md).

     В качестве примера можно привести описания функциональности пользователей (user story), варианты использования и описания других требований в приложении, обеспечивающем работу ресторана. В этом описании можно найти такие термины как "Меню", "Заказ", "Еда", "Цена", "Оплата" и т. д. Можно создать UML-схему классов, определяющую отношения между этими терминами. Это позволит снизить риск возникновения несоответствий в описаниях требований, пользовательском интерфейсе и справочной документации.

### <a name="relationship-to-other-diagrams"></a>Отношение к другим схемам
 UML-схема классов, как правило, создается одновременно с другими схемами моделирования, чтобы предоставить описания используемых типов. В каждом случае физическое представление типов не подразумевается ни одной из схем.

 схема активности

 тип данных, передаваемых через узел объекта.

 типы закреплений ввода и вывода и узлы параметров действий.

 See [UML Activity Diagrams: Guidelines](../modeling/uml-activity-diagrams-guidelines.md).

 Схема последовательностей

 типы параметров и возвращаемые значения сообщений.

 типы линий жизни. Класс линии жизни должен включать операции для всех сообщений, которые он может получить.

 See [UML Sequence Diagrams: Guidelines](../modeling/uml-sequence-diagrams-guidelines.md).

 схема компонентов

 интерфейсы компонента с перечислением их операций.

 See [UML Component Diagrams: Guidelines](../modeling/uml-component-diagrams-guidelines.md).

 Схема вариантов использования

 типы, упомянутые в описаниях целей и шагов варианта использования.

 See [UML Use Case Diagrams: Guidelines](../modeling/uml-use-case-diagrams-guidelines.md).

## <a name="BasicSteps"></a> Basic Steps for Drawing Class Diagrams
 For reference information about the elements on UML class diagrams, see [UML Class Diagrams: Reference](../modeling/uml-class-diagrams-reference.md).

> [!NOTE]
> Detailed steps for creating any of the modeling diagrams are described in [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md).

#### <a name="to-create-a-uml-class-diagram"></a>Создание UML-схемы классов

1. On the **Architecture** menu, choose **New UML or Layer Diagram**.

2. Under **Templates**, choose **UML Class Diagram**.

3. Назовите схему.

4. In **Add to Modeling Project**, select an existing modeling project in your solution, or **Create a New Modeling Project**, and then choose **OK**.

     A new class diagram appears with the **UMLClass Diagram** Toolbox. Панель элементов содержит требуемые элементы и отношения.

#### <a name="to-draw-a-uml-class-diagram"></a>Создание UML-схемы классов

1. To create a type, choose the **Class**, **Interface** or **Enumeration** tool on the Toolbox, and then click a blank part of the diagram. (Если панель элементов не отображается, нажмите клавиши CTRL+ALT+X.)

2. To add attributes or operations to the types, or literals to an enumeration, choose the **Attributes**, **Operations** or **Literals** heading in the type, and press ENTER.

     Можно создать сигнатуру, например `f(x:Boolean):Integer`. See [Attributes and Operations](#AttributesAndOperations).

     Чтобы быстро добавить несколько элементов, дважды нажмите ВВОД в конце каждого элемента. Чтобы переместить элементы вверх или вниз по списку, можно воспользоваться клавишами со стрелками.

3. Чтобы развернуть или свернуть тип, щелкните значок шеврона в левой верхней части типа. You can also expand and collapse the **Attributes** and **Operations** section of a class or interface.

4. Чтобы создать связи ассоциаций, наследования или зависимостей между типами, щелкните соответствующий инструмент, выберите тип источника и укажите тип целевого объекта.

5. To create types in a package, create a package using the **Package** tool, and then create new types and packages within the package. Чтобы скопировать типы и вставить их в пакет также можно использовать команду копирования.

6. Каждая схема — это представление на модели, которое совместно используется другими схемами того же проекта. To see a tree view of the complete model, choose **View**, **Other Windows**, **UML Model Explorer**.

## <a name="UsingTypes"></a> Using Classes, Interfaces, and Enumerations
 Существует три стандартных вида классификаторов, которые доступны на панели элементов. These are referred to as *types* throughout this document.

 ![A class, an enumeration, and an interface](../modeling/media/uml-classguidetypes.png "UML_ClassGuideTypes")

- Use **Classes** (1) to represent data or object types for most purposes.

- Use **Interfaces** (2) in a context where you have to differentiate between pure interfaces and concrete classes that have internal implementations. Различать эти сущности полезно при работе со схемами, целью которых является описание реализации программы. При моделировании пассивных данных или определении концептов для описания пользовательских требований это менее эффективно.

- Use an **Enumeration** (3) to represent a type that has a limited number of literal values, for example `Stop` and `Go`.

  - Добавление значений литералов в перечисление Дайте каждому отдельное имя.

  - При желании каждому значению литерала также можно присвоить численное значение. Open the shortcut menu for the literal in the enumeration, choose **Properties**, and then type a number in the **Value** field in the **Properties** window.

  Дайте каждому типу уникальное имя.

### <a name="getting-types-from-other-diagrams"></a>Получение типов из других схем
 На UML-схеме классов можно отображать типы из другой схемы.

 UML-схема классов

 Можно отображать класс на нескольких UML-схемах классов. When you have created a class on one diagram, drag the class from **UML Model Explorer** onto the other diagram.

 Такой подход эффективен, если необходимо на каждой схеме отобразить определенную группу отношений.

 Например, можно показать связи между элементами "Заказ еды" и "Меню" ресторана на одной схеме, а связи между элементами "Заказ еды" и "Оплата" — на другой.

 Схема компонентов

 If you have defined interfaces on the components in a component diagram, you can drag an interface from **UML Model Explorer** onto the class diagram. На схеме классов можно определить методы, которые входят в интерфейс.

 See [UML Component Diagrams: Guidelines](../modeling/uml-component-diagrams-guidelines.md).

 Схема последовательностей UML

 You can create classes and interfaces from lifelines in a sequence diagram, and then drag the class from **UML Model Explorer** to a UML class diagram. Каждая линия жизни на схеме последовательностей представляет экземпляр объекта, компонента или субъекта.

 To create a class from a lifeline, open the shortcut menu for the lifeline, and then choose **Create Class** or **Create Interface**. See [UML Sequence Diagrams: Guidelines](../modeling/uml-sequence-diagrams-guidelines.md).

## <a name="AttributesAndOperations"></a> Attributes and Operations
 Атрибут (4) — это именованное значение, которое может быть присвоено каждому экземпляру типа. Осуществление доступа к атрибуту не меняет состояние экземпляра.

 Операция (5) — это метод или функция, которая может выполняться экземплярами типа. Она может возвращать значение. If its **isQuery** property is true, it cannot change the state of the instance.

 To add an attribute or operation to a type, open the shortcut menu for the type, choose **Add**, and then choose **Attribute** or **Operation**.

 To see its properties, open the shortcut menu for the attribute or operation, and then choose **Properties**. The properties appear in the **Properties** window.

 To see the properties of an operation's parameters, choose <strong>[…]</strong>in the **Parameters** property. Отобразится новое диалоговое окно свойств.

 Дополнительные сведения обо всех свойствах, которые можно задать, см. в следующих разделах:

- [Свойства атрибутов на схемах классов UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md)

- [Свойства операций на схемах классов UML](../modeling/properties-of-operations-on-uml-class-diagrams.md)

### <a name="types-of-attributes-and-operations"></a>Типы атрибутов и операций
 Each *Type* of an attribute or operation, and each parameter type, can be one of the following:

- **(none)** - You can leave a type unspecified in the signature by omitting the preceding colon (`:`).

- One of the standard primitive types: **Boolean**, **Integer**, **String**.

- Тип, определенный в модели.

- A parameterized value of a template type, written Template\<Parameter>. See [Template Types](#Templates).

  Также можно записать имя типа, который еще не был определен в модели. The name will be listed under **Unspecified Types** in UML Model Explorer.

> [!NOTE]
> Если впоследствии в модели определяется класс или интерфейс этого имени, прежние атрибуты и операции все равно относятся к элементу в разделе "Незаданные типы". Если нужно изменить их так, чтобы они относились к новому классу, необходимо открыть каждый атрибут или операцию и сбросить тип, выбирая новый класс из раскрывающегося меню.

#### <a name="multiple-types"></a>Несколько типов
 Можно задать кратность любого атрибута, операции или типа параметров.

 Допустимы следующие значения.

 `[1]`

 Одно значение заданного типа. Это значение по умолчанию.

 `[0..1]`

 **Null** or a value of the given type.

 `[*]`

 Коллекция, в состав которой может входить неограниченное число экземпляров заданного типа.

 `[1..*]`

 Коллекция хотя бы одного экземпляра заданного типа.

 `[n..m]`

 Коллекция, в которую входит от `n` до `m` экземпляров заданного типа.

 Если кратность превышает 1, можно задать следующие свойства.

- **IsOrdered** - If true, the collection has a defined order.

- **IsUnique** - If true, there are no duplicate values in the collection.

### <a name="visibility"></a>Видимость
 *Visibility* indicates whether the attribute or operation can be accessed outside the class definition. Допустимы следующие значения.

 **Public**

 **+**

 Возможен доступ изо всех других типов.

 **Закрытые**

 **-**

 Доступ открыт только для внутреннего определения этого типа.

 **Пакет**

 **~**

 Возможен доступ только внутри пакета, который содержит данный тип, а также в любых пакетах, явно импортирующих его. See [Defining Namespaces and Packages](#Packages).

 **Protected**

 **#**

 Доступ открыт только данному типу и всем типам, которые его наследуют. See [Inheritance](#Inheritance).

### <a name="setting-the-signature-of-an-attribute-or-an-operation"></a>Задание сигнатуры атрибута или операции
 Сигнатура атрибута или операции — это коллекция свойств, включающая видимость, имя, параметры (для операций) и тип.

 Сигнатуру можно создать непосредственно на схеме. Щелкните атрибут или операцию, чтобы выделить элемент, затем повторно щелкните его.

 Создайте сигнатуру в следующей форме.

```
visibility attribute-name : Type
```

 \- или -

```
visibility operation-name (parameter1 : Type1, ...) : Type
```

 Пример:

```
+ AddItem (item : MenuItem, quantity : Integer) : Boolean
```

 Используйте краткую форму значения свойства visibility. Значение по умолчанию — `+` (открытый).

 Каждый тип может представлять собой типы, определенные в модели, стандартные типы (такие как Integer или String) или имя нового типа, который еще не был определен.

> [!NOTE]
> Если в списке параметров создается имя без типа, оно представляет собой имя параметра, а не типа. В этом примере MenuItem и Integer являются именами двух параметров с незаданным типами.
>
> `AddItem(MenuItem, Integer) /* parameter names, not types! */`

 Чтобы задать в сигнатуре кратность типа, запишите кратность в квадратных скобках после имени типа. Например, как показано ниже.

```
+ AddItems (items : MenuItem [1..*])
+ MenuContent : MenuItem [*]
```

 Если атрибут или операция статична, имя атрибута или операции отображается в сигнатуре подчеркнутым. Если атрибут или операция абстрактна, имя отображается курсивом.

 However, you can only set the **Is Static** and **Is Abstract** properties in the **Properties** window.

#### <a name="full-signature"></a>Полная сигнатура
 При редактировании сигнатуры атрибута или операции в конце строки и после каждого параметра могут отображаться дополнительные свойства. Они отображаются заключенными в фигурные скобки {…}. Эти свойства можно редактировать и добавлять. Пример:

```
+ AddItems (items: MenuItem [1..*] {unique, ordered})
+ GetItems (filter: String) : MenuItem [*] {ordered, query}
```

 Список содержит следующие свойства.

 `unique`

 **Is Unique**

 В коллекции нет повторяющихся значений. Применимо к типам с кратностью больше 1.

 `ordered`

 **Is Ordered**

 Коллекция — это последовательность. Если значение false, не существует определенного первого элемента. Применимо к типам с кратностью больше 1.

 `query`

 **Is Query**

 Операция не меняет состояние экземпляра. Применимо только к операциям.

 `/`

 **Is Derived**

 Атрибут вычисляется из значений других атрибутов или ассоциаций.

 "/" отображается перед именем атрибута. Пример:

```
/TotalPrice: Integer
```

 Как правило, полная сигнатура отображается на схеме, только когда она редактируется. По завершении редактирования дополнительные свойства скрываются. If you want to see the full signature all the time, open the shortcut menu for the type, and then choose **Show Full Signature**.

## <a name="Associations"></a> Drawing and Using Associations
 Используйте ассоциацию, чтобы представить любые виды отношений между двумя элементами, независимо от того, как эта связь реализуется в программе. Например, можно использовать ассоциацию, чтобы представить указатель в C#, отношение в базе данных или перекрестную ссылку одной части XML-файла на другую. Может представлять связь между объектами в реальном мире, например землей и солнцем. Ассоциация не показывает, как представлена ссылка, а только свидетельствует о наличии сведений.

### <a name="properties-of-an-association"></a>Свойства ассоциации
 После создания ассоциации необходимо задать ее свойства. Open the shortcut menu for the association, and then choose **Properties**.

 In addition to the properties of the association as a whole, each *role*, that is, each end of the association, has some properties of its own. To view them, expand the **First Role** and **Second Role** properties.

 Некоторые свойства каждой роли напрямую видны на схеме. Они приведены ниже:

- Имя роли. Отображается на соответствующем окончании ассоциации на схеме. You can set it either on the diagram or in the **Properties** window.

- **Multiplicity**, which defaults to **1**. Это значение также отображается на схеме рядом с соответствующим окончанием ассоциации.

- **Aggregation**. Отображается в форме ромбовидной фигуры на одном окончании соединителя. Можно использовать его для указания, что экземпляры в обобщающей роли владеют экземплярами другой роли или содержат их.

- **Is Navigable**. Если имеет значение true только для одной роли, в направлении перехода отображается стрелка. С помощью этого свойства можно показать возможности перехода по ссылкам и связи в базе данных в программе.

  For the full details of these and other properties, see [Properties of associations on UML class diagrams](../modeling/properties-of-associations-on-uml-class-diagrams.md).

### <a name="navigability"></a>Возможность перехода
 Когда изображается ассоциация, на одном конце у нее стрелка, обозначающая, что ассоциация дает возможность перехода в этом направлении. Это удобно, если схема классов представляет классы ПО, а ассоциации представляют указатели или ссылки. Но если схема классов представляет сущности и отношения или бизнес-концепции, возможность перехода показывать не обязательно. В таком случае можно изображать ассоциации без стрелок. You can do so by setting the **Is Navigable** property on both ends of the association to True.

### <a name="attributes-and-associations"></a>Атрибуты и ассоциации
 Ассоциация — это графический способ представления атрибута. Например, вместо того чтобы создавать класс "Ресторан" с атрибутом типа "Меню", можно создать ассоциацию из элементов "Ресторан" и "Меню".

 Каждое имя атрибута становится именем роли. Оно отображается на противоположном типу-владельцу окончании ассоциации. Например, обратите внимание на `myMenu` на этой иллюстрации.

 Как правило, рекомендуется использовать атрибуты только для типов, которые не отображаются на схеме, например для типов-примитивов.

 ![Equivalent association and attributes](../modeling/media/uml-classguideattrib.png "UML_ClassGuideAttrib")

## <a name="Inheritance"></a> Наследование
 Use the **Inheritance** tool to create the following relationships:

- A *generalization* relationship between a specialized type and a general type

   \- или -

- A *realization* relation between a class and an interface that it implements.

  Невозможно создавать циклы в отношениях наследования.

### <a name="generalization"></a>Обобщение
 Обобщение означает, что специализирующий или производный тип наследует атрибуты, операции и ассоциации общего или базового типа.

 Общий тип отображается на окончании отношения с наконечником стрелки.

 Наследуемые операции и атрибуты, как правило, не отображаются в специализирующих типах. Однако можно добавить наследуемые операции в список операций специализирующего типа. Такой подход эффективен, если необходимо переопределить некоторые свойства операции в специализирующем типе, либо если необходимо указать, что переопределять свойства нужно с помощью реализующего кода.

##### <a name="to-override-an-operations-definition-in-a-specializing-type"></a>Переопределение определения операции в специализирующем типе

1. Щелкните отношение обобщения.

    Оно станет выделенным, и рядом с ним отобразится тег действия.

2. Click the Action tag, and then click **Override Operations**.

    The **Override Operations** dialog box appears.

3. Select the operations that you want to appear in the specializing type, and then click **OK**.

   Выделенные операции теперь отображаются в специализирующем типе.

### <a name="realization"></a>Реализация
 Реализация означает, что класс реализует атрибуты и операции, заданные в интерфейсе. Интерфейс находится на окончании соединителя с наконечником стрелки.

 При создании соединителя реализации операции интерфейса автоматически реплицируются в реализующем классе. При добавлении в интерфейс новых операций они реплицируются в реализующих классах интерфейса.

 После создания отношения реализации можно преобразовать его в обозначение без описания операций. Right-click the relationship and choose **Show as Lollipop**.

 Так можно показать интерфейсы, реализуемые классом, не усложняя схемы классов многочисленными ссылками реализации. Также на отдельных схемах можно показать интерфейс и реализующие его классы.

 ![Realization shown with conector and lollipop](../modeling/media/uml-classguiderealize.png "UML_ClassGuideRealize")

## <a name="Templates"></a> Template Types
 Можно определить общий тип или тип шаблона, параметры которого задаются другими типами и значениями.

 Например, можно создать общий тип Dictionary, параметры которого задаются ключевыми типами и типами значений.

 ![Template class with two parameters](../modeling/media/uml-classguidetemplate1.png "UML_ClassGuideTemplate1")

#### <a name="to-create-a-template-type"></a>Создание типа шаблонов

1. Создайте класс или интерфейс. Это ваш тип шаблонов. Присвойте ему соответствующее имя, например `Dictionary`.

2. Open the shortcut menu for the new type, and then choose **Properties**.

3. In the **Properties** window, click **[…]** in the **Template Parameters** field.

    The **Template Parameter Collection Editor** dialog box appears.

4. Выберите **Добавить**.

5. В свойстве "Имя" задайте имя параметра для типа шаблонов, например `Key`.

6. Set **Parameter Kind**. The default is **Class**.

7. If you want the parameter to accept only derived classes of a particular base class, set **Constrained Value** to the base class that you want.

8. Add as many parameters as you need, then choose **OK**.

9. Добавьте атрибуты и операции в тип шаблонов так же, как при работе с другими классами.

     You can use parameters whose kind is **Class**, **Interface** or **Enumeration** in the definition of attributes and operations. Например, используя классы параметров `Key` и `Value`, можно определить эту операцию в `Dictionary`.

     `Get(k : Key) : Value`

     You can use a parameter whose kind is **Integer** as a bound in a multiplicity. Например, максимально допустимое значение параметра Integer можно использовать для определения кратности атрибута в виде `[0..max]`.

   Созданные типы шаблонов можно использовать для определения привязок шаблонов.

   ![A  class bound from the Dictionary template](../modeling/media/uml-classguidetemplate2.png "UML_ClassGuideTemplate2")

#### <a name="to-use-a-template-type"></a>Использование типа шаблонов

1. Создайте новый тип, например `AddressTable`.

2. Open the shortcut menu for the new type, and then choose **Properties**.

3. In the **Template Binding** property, select the template type, for example `Dictionary`, from the drop-down list.

4. Expand the **Template Binding** property.

     Отображается строка для каждого параметра типа шаблонов.

5. Задайте подходящее значение для каждого параметра. Например, задайте для параметра `Key` класс `Name`.

## <a name="Packages"></a> Packages
 На UML-схеме классов можно просматривать пакеты. Пакет — это контейнер для других элементов модели. Внутри пакета можно создать любой элемент. На схеме элементы внутри пакета перемещаются по схеме, если перемещается пакет.

 Чтобы скрыть или отобразить содержимое пакета, можно использовать элемент управления "развернуть/свернуть".

 See [Define packages and namespaces](../modeling/define-packages-and-namespaces.md).

## <a name="generating"></a> Generating Code from UML Class Diagrams
 Чтобы приступить к реализации классов на схеме классов UML, можно создать код C# или настроить шаблоны создания кода. Чтобы приступить к созданию кода с помощью предоставленных шаблонов C#:

- Open the shortcut menu for the diagram or an element, choose **Generate Code**, and then set the necessary properties.

     For more information about how to set these properties and customize the provided templates, see [Generate code from UML class diagrams](../modeling/generate-code-from-uml-class-diagrams.md).

## <a name="see-also"></a>См. также раздел
 [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md) [UML Class Diagrams: Reference](../modeling/uml-class-diagrams-reference.md) [Model user requirements](../modeling/model-user-requirements.md) [UML Component Diagrams: Reference](../modeling/uml-component-diagrams-reference.md) [UML Sequence Diagrams: Reference](../modeling/uml-sequence-diagrams-reference.md) [UML Use Case Diagrams: Reference](../modeling/uml-use-case-diagrams-reference.md) [UML Component Diagrams: Reference](../modeling/uml-component-diagrams-reference.md)
