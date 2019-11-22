---
title: 'UML Use Case Diagrams: Guidelines | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- diagrams - modeling, use case
- UML, use case diagrams
- diagrams - modeling, UML use case
- use case diagrams
- UML diagrams, use case
ms.assetid: b1ae8ed0-d00b-4f9b-8e23-733e09e81e9b
caps.latest.revision: 38
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7c9ccd5285f9a2744704c0ee13094a1dac31c53b
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302835"
---
# <a name="uml-use-case-diagrams-guidelines"></a>UML-схемы вариантов использования: правила работы
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio, you can draw a *use case diagram* to summarize who uses your application or system, and what they can do with it. To create a UML use case diagram, on the **Architecture** menu, click **New UML or Layer Diagram**.

 For a video demonstration, see [Organizing Features into Use Cases](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-2-organizing-features-into-use-cases).

 Чтобы узнать, какие версии Visual Studio поддерживают эту функцию, см. раздел [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 С помощью схемы вариантов использования можно обсудить и передать следующие сведения:

- Сценарии, в которых система или приложение взаимодействуют с людьми, организациями или внешними системами.

- Цели, которых она помогает добиться этим субъектам.

- Область действия системы.

  На схеме вариантов использования не отображаются подробности о вариантах использования: на ней представлены только некоторые отношения между вариантами использования, субъектами и системами. В частности, схема не показывает порядок выполнения шагов для достижения цели каждого из вариантов использования. Эти сведения можно описать в других схемах и документах, которые можно связать с каждым вариантом использования. For more information, see [Describing Use Cases in Detail](#Details) in this topic.

  Описания для вариантов использования будут использовать несколько терминов, связанных с доменом, в котором работает система, например продажи, меню, клиент и т. д. Очень важно четко определить эти термины и их отношения, и это можно сделать с помощью схемы классов UML. For more information, see [UML Class Diagrams: Guidelines](../modeling/uml-class-diagrams-guidelines.md).

  Варианты использования фигурируют только в функциональных требованиях к системе. Другие требования, такие как бизнес-правила, требования к качеству обслуживания и ограничения реализации, должны быть представлены отдельно. Архитектура и подробности о внутренней структуре также нужно описывать отдельно. For more information about how to define user requirements, see [Model user requirements](../modeling/model-user-requirements.md).

  Примеры, используемые в этом разделе, относятся к веб-сайту, на котором клиенты могут заказывать еду из местных ресторанов.

  ![Elements in a use case diagram](../modeling/media/uml-ucovactor.png "UML_UCOvActor")

- An *actor* (1) is a class of person, organization, device, or external software component that interacts with your system. Example actors are **Customer**, **Restaurant**, **Temperature Sensor**, **Credit Card Authorizer.**

- A *use case* (2) represents the actions that are performed by one or more actors in the pursuit of a particular goal. Example use cases are **Order Meal**, **Update Menu**, **Process Payment**.

   На схеме вариантов использования варианты использования ассоциированы (3) с выполняющими их субъектами.

- Your *system (4)* is whatever you are developing. Это может быть небольшой программный компонент, чьи субъекты являются просто другими программными компонентами; или это может быть полноценное приложение; или это может быть большой распределенный набор приложений, развернутый на множестве компьютеров и устройств. Example subsystems are **Meal Ordering Website**, **Meal Delivery Business**, **Website Version 2**.

   Схема вариантов использования может показать, какие варианты использования поддерживаются системой или ее подсистемами.

## <a name="BasicSteps"></a> Basic Steps for Drawing Use Case Diagrams

> [!NOTE]
> Detailed steps for creating any of the modeling diagrams are described in [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md).

#### <a name="to-create-a-new-use-case-diagram"></a>Создание новой схемы вариантов использования

1. On the **Architecture** menu, click **New UML or Layer Diagram**.

2. Under **Templates**, click **UMLUse Case Diagram**.

3. Назовите схему.

4. In **Add to Modeling Project**, select an existing modeling project in your solution, or **Create a New Modeling Project**, and then click **OK**.

#### <a name="to-draw-a-use-case-diagram"></a>Создание схемы вариантов использования

1. Drag **Subsystem** boundaries from the toolbox onto the diagram, to represent either your whole system or its major components.

    - Вы можете нарисовать схему вариантов использования без границ системы, если не хотите описывать, какие варианты использования поддерживаются вашей системой или ее компонентами.

    - При необходимости перетащите угол системы, чтобы сделать ее больше.

    - Переименуйте ее соответствующим образом.

2. Drag **Actors** from the toolbox onto the diagram (placing them outside any system boundary).

    - Субъекты представляют классы пользователей, организаций и внешних систем, взаимодействующие с вашей системой.

    - Переименуйте их. For example: **Customer, Restaurant, Credit card agency.**

3. Drag **Use Cases** from the toolbox onto the appropriate systems.

    - Варианты использования представляют действия, выполняемые субъектами с помощью системы.

    - Переименуйте их, используя названия, понятные этим субъектам. Не используйте названия, имеющие отношение к вашему коду. For example: **Order Meal, Pay for Meal, Deliver Meal**.

    - Begin with major transactions such as **Order Meal**, leaving until later smaller interactions such as **Select Menu Item**.

    - Поместите каждый вариант использования в систему или крупную подсистему, поддерживающую его (игнорируя различные представления и компоненты, используемые только для связи с пользователем).

    - Можно создать вариант использования за пределами границы системы, чтобы показать, что он не поддерживается системой, возможно, в определенной версии или определенном выпуске.

4. Click **Association** on the toolbox, then a use case, and then an actor that participates in the use case. Аналогичным образом свяжите каждый субъект с его вариантами использования.

5. Structure the use cases with the **Include**, **Extend** and **Generalization** relationships. Чтобы создать каждую из этих связей, щелкните инструмент, затем источник вариантов использования и затем целевой объект. See the following section titled [Structuring Use Cases](#Structuring).

6. Опишите варианты использования более подробно. See the following section titled [Describing Use Cases in Detail](#Details).

7. Нарисуйте отдельные схемы, чтобы сконцентрироваться на различных подсистемах или разных группах связанных вариантов использования. Все схемы в одном проекте моделирования являются представлениями одной модели.

## <a name="Actors"></a> Drawing Actors and Use Cases
 Основное назначение схемы вариантов использования заключается в том, чтобы показать, кто взаимодействует с системой и каких основных целей он при этом достигает.

- Create **Actors** to represent classes of people, organizations, other systems, software or devices that interact with your system or subsystem.

  - To learn how to draw actors and other elements, see [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md).

  - Для каждого отдельного набора целей определите субъекты по типу или роли, несмотря на то, что физические лица или сущности могут быть одинаковыми. Например, ресторан и клиент — это отдельные субъекты, хотя сотрудник ресторана иногда может быть клиентом.

- Create **Use Cases** for each of the goals that each actor seeks to achieve with the system.

  - Назовите и опишите варианты использования понятными субъекту словами, а не терминами реализации.

- Use **Associations** to link actors to use cases.

### <a name="inheritance-between-actors"></a>Наследование между субъектами
 ![Use case diagram showing inheritance](../modeling/media/uml-ucguideinherit.png "UML_UCGuideInherit")

 You can draw a **Generalization** link between Actors. Специализированный субъект, такой как клиент клуба Club Customer в данном примере, наследует варианты использования обобщенного субъекта, такого как клиент Customer. Стрелка должна указывать на более общий субъект, например Customer. При создании связи сначала укажите более специализированный субъект.

 Специализированный субъект может иметь свои собственные дополнительные варианты использования, которые недоступны другим субъектам.

> [!CAUTION]
> Вам не следует создавать циклы отношений обобщения, которые вызывают обобщение субъектом самого себя. Циклы могут стать причиной ошибок.

### <a name="alternative-actor-icons"></a>Другие значки субъектов
 Можно использовать настраиваемые значки для представления субъекта, а не стандартное схематичное изображение. Например, можно изменить его так, чтобы он напоминал устройство, ресторан, банк и т. д.

##### <a name="to-change-the-appearance-of-an-actor"></a>Изменение внешнего вида субъекта

1. Right-click the actor and then click **Properties**.

     Откроется окно **Свойства** .

2. Set the **Image Path** property to the location of an image file.

    - Можно использовать любой из нескольких форматов изображения, включая GIF, JPG и BMP.

    - Используйте файл, включенный в систему управления версиями решения или проекта, чтобы он оставался доступным в случае перемещения или копирования решения.

3. Чтобы реплицировать этот внешний вид на других схемах вариантов использования, скопируйте субъект и вставьте его в другую схему.

    - Изменение изображения применяется только к представлению на определенной схеме. Оно не применяется к элементу базовой модели. Если перетащить субъект из обозревателя моделей UML на другую схему, он будет отображаться как стандартное схематическое изображение.

### <a name="multiplicities-between-actors-and-use-cases"></a>Кратности между субъектами и вариантами использования
 The association between an actor and a use case can show a *multiplicity* at each end.

 ![Use case one to one with actor](../modeling/media/uml-ucguidemulti1.png "UML_UCGuideMulti1")

> [!NOTE]
> The multiplicities of an association on a use case diagram are hidden if they are both **1**.

 By default, each multiplicity is **1**. В строгой интерпретации модели кратность 1 означает, что, например, только один клиент участвует в заказе каждого блюда и что каждый клиент заказывает только одно блюдо за раз.

 Эти кратности можно изменить.

 Пример:

 ![Use case showing many to many multiplicity](../modeling/media/uml-ucguidemulti2.png "UML_UCGuideMulti2")

- To state that several actors of the same class can take part in a single occurrence of a use case, set the multiplicity at the actor end of the association to **1..\*** .

   На рисунке один или несколько ресторанов могут участвовать в выполнении одного заказа.

- To show that each actor can participate at the same time in several occurrences of a use case, set the multiplicity at the use case end of the association to **\*** .

   На рисунке каждый ресторан может одновременно работать на выполнением нескольких заказов.

##### <a name="to-set-multiplicities-on-an-association"></a>Задание кратностей в ассоциации

1. Right-click the association and then click **Properties**.

2. Expand either **First Role** or **Second Role**.

    *Role* means the element at one end of the association.

3. Задайте свойство кратности, выбрав значение из списка:

   - **1** to state that exactly one instance of this role participates in each link.

   - **1..\*** to state that one or more instance of this role participate in each link.

   - **0..1** to state that participation is optional.

   - **\*** to state that zero or more instances of this role participate in the link.

> [!NOTE]
> Многие команды не размещают сведения о кратностях на схемах вариантов использования, оставляя для них значение по умолчанию 1. Вместо этого они предоставляют информацию в отдельных описаниях для вариантов использования. В этом случае все кратности на схемах вариантов использования будут скрыты.

### <a name="using-an-actor-or-use-case-on-multiple-diagrams"></a>Использование субъекта или варианта использования на нескольких схемах
 Можно отобразить одни и те же субъекты и варианты использования на нескольких схемах. Пример:

- Разные варианты использования, в которых участвует один субъект, можно описать в разных схемах.

- Можно использовать одну схему, чтобы показать субъекты и подсистемы, с которыми связан вариант использования, и другую схему, чтобы показать структурирование варианта использования на включенный и расширенный варианты использования.

##### <a name="to-show-the-same-actor-or-use-case-on-different-diagrams"></a>Отображение одного субъекта или варианта использования на разных схемах

1. Создайте субъект или вариант использования на одной схеме.

2. Создайте другую схему вариантов использования.

3. Drag an actor or use case off **Model Explorer** onto the new diagram.

    > [!NOTE]
    > Если поместить на новой схеме субъект и вариант использования, которые уже связаны, ассоциация между ними автоматически отображается на новой схеме.

## <a name="Details"></a> Describing use cases in detail
 Вариант использования представляет следующее:

- A goal of an actor in using the system, such as **Buy a Meal**; and

- One or more *scenarios*, that is, sequences of steps performed in pursuing the goal, such as: {**Order Meal, Pay, Deliver**}. In addition to success scenarios, there might be several exception or failure scenarios, such as **Credit Card Rejected**.

  Вариант использования можно описать с различными уровнями детализации. На раннем этапе разработки достаточно имени на схеме вариантов использования.  Позже можно написать более подробные описания сценариев.

  В Visual Studio Ultimate вариант использования можно описать несколькими способами, которые можно использовать как отдельно, так и совместно.

- Свяжите вариант использования с другой схемой или схемами в проекте.

  - Схема деятельности позволяет пояснить более сложный процесс, где присутствуют циклы, ветви и параллельные потоки. Она также может отображать поток данных между разными частями процесса. For more information, see [UML Activity Diagrams: Guidelines](../modeling/uml-activity-diagrams-guidelines.md).

  - Схема последовательностей позволяет описывать сложные серии взаимодействий между разными субъектами. Ее также можно использовать, чтобы показать, что происходит в системе при реагировании на каждый вариант использования. For more information, see [UML Sequence Diagrams: Guidelines](../modeling/uml-sequence-diagrams-guidelines.md).

- Свяжите вариант использования со страницей, разделом или абзацем OneNote, который подробно описывает этот вариант использования.

- Свяжите вариант использования с документом Word, в которой используется текст, снимки экрана и т. п. для описания сценариев варианта использования. For more information, see [Model user requirements](../modeling/model-user-requirements.md).

#### <a name="to-link-a-use-case-to-a-diagram-or-file-in-the-same-solution"></a>Связывание варианта использования со схемой или файлом в том же решении

1. Создайте схему, например схему последовательностей или схему деятельности, чтобы проиллюстрировать сценарий варианта использования.

2. Вернитесь к схеме вариантов использования.

3. Перетащите схему или файл из обозревателя решений на пустую часть схемы вариантов использования.

4. Connect from the artifact to the use case using a **Dependency**.

#### <a name="to-link-to-a-solution-file-such-as-a-word-document-or-powerpoint-presentation"></a>Связывание с файлом решения, таким как документ Word или презентация PowerPoint

1. Составьте документ, использующий текст, снимки экрана и т. п., чтобы описать сценарий варианта использования.

2. Добавьте документ в решение.

    1. Переместите документ Word в папку Windows, в которой сохранено решение.

    2. In Solution Explorer, right-click the solution, point to **Add**, and then click **Existing Item**.

    3. Navigate to the Word document and click **Add**.

         Документ Word отображается в папке решения в обозревателе решений.

3. Перетащите документ Word из обозревателя решений на пустую часть схемы вариантов использования.

     Появится новый артефакт.

4. Connect from the artifact to the use case using a **Dependency**.

#### <a name="to-link-to-a-shared-document-onenote-element-or-web-page"></a>Связывание с общим документом, элементом OneNote или веб-страницей

1. Получите URL-адрес общего элемента. This can be, for example, a network file path beginning '\\\\', or a web page or Sharepoint URL beginning 'http://', or a link to a OneNote section, page, or paragraph beginning 'onenote:'.

2. In the Toolbox, click **Artifact** and then click in the use case diagram.

3. With the new artifact selected, type or paste the URL into the **Hyperlink** property.

> [!NOTE]
> Дважды щелкните артефакт, чтобы открыть схему или документ, с которыми он связан.

### <a name="linking-use-cases-to-work-items"></a>Связывание вариантов использования с рабочими элементами
 If your project uses [!INCLUDE[vstsTfsRosarioLong](../includes/vststfsrosariolong-md.md)] and you have [!INCLUDE[esprtfc](../includes/esprtfc-md.md)], you can link each use case to a work item in [!INCLUDE[esprfound](../includes/esprfound-md.md)]. To learn how to make these links, see [Link model elements and work items](../modeling/link-model-elements-and-work-items.md).

 Это позволяет выполнять следующие действия:

- описание варианта использования в связанном рабочем элементе. В частности, если в проекте используется формальный шаблон процессов Visual Studio, можно связать вариант использования с рабочим элементом. Этот тип рабочего элемента предоставляет поля для описания целей и сценариев варианта использования.

- Связывание тестовых случаев с вариантом использования, чтобы можно было получить отчеты о том, насколько разрабатываемый код реализует вариант использования.

- Связывание задач с вариантом использования, чтобы отслеживать ход выполнения разработки.

## <a name="Structuring"></a> Structuring Use Cases
 Следует попытаться описать поведение системы лишь с помощью нескольких основных вариантов использования. Каждый крупный вариант использования определяет основную цель, достигаемую субъектом, например приобретение продукции или с точки зрения поставщика — предоставление продукции на продажу.

 После уточнения этих целей можно переходить к более подробному рассмотрению способов достижения каждой цели и различий в основных целях.

 Старайтесь не разбивать варианты использования на слишком много деталей. Варианты использования затрагивают впечатления пользователей от взаимодействия с системой, а не ее внутреннее функционирование. Кроме того, обычно более эффективно создавать предварительные рабочие версии кода, а не тратить время на структурирование вариантов использования с повышенной детализацией.

 На схеме вариантов использования можно подвести итог по отношениям между основной и дополнительной областями действия. В следующих раздела описано следующее:

- [Showing the details of a use case with Include](#Include)

- [Sharing goals with Generalization](#Inheritance)

- [Separating out variant cases with Extend](#Extend)

### <a name="Include"></a> Showing the details of a use case with Include
 Use an **Include** relation to show that one use case describes some of the detail of another. In the illustration, **Order a Meal** includes **Pay**, **Choose Menu**, and **Choose Menu Item**. Каждый из включенных и более подробных вариантов использования представляет собой действие, которое может потребоваться выполнить субъекту или субъектам для достижения общей цели включающего варианта использования. Стрелка должна указывать на более подробный включенный вариант использования.

> [!CAUTION]
> Не рекомендуется создавать циклы отношений включения, которые приводят к тому, что варианты использования включают сами себя. Циклы могут стать причиной ошибок.

 Включенные варианты использования можно использовать совместно. In the example, the **Order a Meal** and **Subscribe to Reviews** use cases both include **Pay**.

 ![Use cases decomposed with include](../modeling/media/uml-ucguideinclude.png "UML_UCGuideInclude")

 Цель и сценарии включенного варианта использования иметь смысл независимо друг от друга, чтобы их можно было включить в варианты использования, созданные позже.

 Разделение вариантов использования на включающие и включенные части позволяет достичь следующих целей:

- Структурирование описаний вариантов использования на разные уровни детализации.

- Предотвращение дублирования общих сценариев в разных вариантах использования.

#### <a name="Steps"></a> Defining the order of the detailed steps
 Схема вариантов использования ничего не говорит о порядке, в которой следует выполнять более подробные шаги, а также о том, является ли каждый из них обязательным всегда.

 To make the order of the steps clear, you can use an **Artifact** to attach a separate document to the including use case. В следующем примере схема деятельности прикреплена к варианту использования для заказа еды. Кроме того, можно использовать текстовый документ со списком шагов или последовательностью снимков экрана. For more information, see [Describing Use Cases in Detail](#Details).

 Обратите внимание на эти соглашения именования при использовании схемы деятельности:

- Имя целого действия совпадает с включающим вариантом использования.

- Действия на схеме деятельности имеют те же имена, что и включенные варианты использования.

  For more information, see [UML Activity Diagrams: Guidelines](../modeling/uml-activity-diagrams-guidelines.md).

  ![Use case steps shown in linked activity diagram](../modeling/media/uml-ucguidesteps.png "UML_UCGuideSteps")

### <a name="Inheritance"></a> Sharing goals with Generalization
 Use a Generalization relation to show that a *specialized* use case is a particular way to achieve the goals expressed by another *general* use case. Стрелка должна указывать на более общий вариант использования.

 ![Use cases showing the generalization relation](../modeling/media/uml-ucguidegeneral.png "UML_UCGuideGeneral")

 For example, **Pay** generalizes **Pay by Credit Card** and **Pay by Cash**.

> [!CAUTION]
> Вам не следует создавать циклы отношений обобщения, которые вызывают обобщение субъектом самого себя. Циклы могут стать причиной ошибок.

 Специализированные варианты использования помогают показать различные способы для достижения системой одной и той же цели.

 Считается, что специализированные варианты использования наследуют цели и субъекты от общего варианта использования. Общий вариант использования не обязательно имеет собственные сценарии; его специализации описывают различные пути для достижения целей.

##### <a name="to-refactor-common-goals-from-two-or-more-use-cases"></a>Рефакторинг общих целей из двух или более вариантов использования

1. Создайте и назовите новый общий вариант использования.

2. Create a **Generalization** relation with the large arrow pointing at the new general use case.

    1. Click **Generalization** in the toolbox.

    2. Click a specialized use case (**Pay by Credit Card** in the example).

    3. Click the general use case (**Pay** in the example).

3. Если описаны цели для специализированных вариантов использования, переместите общие части в описание общего варианта использования.

4. Субъекты, которые являются общими для специализированных вариантов использования, можно переместить общий вариант использования.

### <a name="Extend"></a> Separating variant cases with Extend
 Используйте связь расширения, чтобы показать, что при определенных обстоятельствах один вариант использования может добавлять функциональные возможности в другой. Стрелка должна указывать на основной, расширенный вариант использования.

 ![One use case extending another](../modeling/media/uml-ucguideextend.png "UML_UCGuideExtend")

> [!CAUTION]
> Вам не следует создавать циклы отношений расширения, которые вызывают обобщение субъектом самого себя. Циклы могут стать причиной ошибок.

 For example, the **Login** use case of a typical Web site can include **Register New User** - but only when the user does not already have an account.

##### <a name="to-separate-a-use-case-into-main-and-extending-parts"></a>Разделение варианта использования на основную и расширенную части

1. Создайте и назовите новый расширенный вариант использования.

2. Create an **Extend** relation with the arrow pointing at the extended use case.

   1. Click **Extend** in the toolbox.

   2. Click the extending use case (**Register New User** in the example).

   3. Click the extended use case (**Login** in the example).

       > [!NOTE]
       > Не рекомендуется создавать на схеме цикл отношений расширения. Вариант использования не должен быть расширением самого себя.

3. Если вы уже создали сценарии для расширенного варианта использования, переместите соответствующие шаги в сценарий расширения.

4. The description of the extension (**Register New User** in the example) should include details of where in the main use case scenarios it will occur, and under what circumstances. Это можно рассматривать как описание основного варианта.

   Вариант использования расширения представляет шаги сценария, которые в противном случае были бы частью сценариев основного варианта использования. Сценарий и цель расширения всегда считываются в контексте основного варианта использования, поэтому они обязаны иметь значение при независимом использовании.

   Разделение расширений может быть полезным при описании следующих ситуаций.

- Имеются дополнительные субъекты, участвующие только в случае использования расширения. Например, администратор должен утвердить регистрацию клиента на веб-сайте.

- Отдельная подсистема обрабатывает вариант использования расширения.

- Это расширение будет доступно только в определенных версиях системы. Каждую версию можно показать как отдельную подсистему на схеме вариантов использования.

## <a name="Subsystems"></a> Using Subsystem Boundaries
 Используйте границу подсистемы, чтобы показать, какие варианты использования находятся в области действия системы.

#### <a name="to-draw-a-subsystem-boundary"></a>Рисование границы подсистемы

1. In the toolbox, click **Subsystem**, then click the diagram.

    На схеме появляется подсистема.

2. Перетащите углы подсистемы, чтобы изменить ее размер.

3. Перетащите имеющиеся варианты использования в подсистему или из нее, чтобы изменить ее содержимое.

   \- или -

   To create a new use case directly in a subsystem, click **Use Case** in the toolbox, then click inside the subsystem.

> [!NOTE]
> The **Subjects** property of a use case indicates what subsystem it is contained within.

### <a name="use-cases-outside-the-system-scope"></a>Варианты использования за пределами области действия системы
 Часто бывает полезно включить в схему варианты использования, которые являются частью бизнеса, но не затрагиваются разрабатываемой системой. Это помогает разработчикам понять контекст своей работы. Например, доставку еды можно отображать как вариант использования, включающий субъекты ресторана и клиента, но выходящий за пределами ответственности веб-сайта заказа еды.

### <a name="multiple-subsystems"></a>Несколько подсистем
 Можно создать несколько границ подсистем, чтобы показать, как разные варианты использования обрабатываются различными компонентами системы. For example, **Add Restaurant Appraisal** may be dealt with on a separate forum Web site. Помните, что схема вариантов использования должна обрабатывать то, что видит пользователь. Если нужно описать внутреннее разделение работы в системе, рекомендуется использовать схему компонентов.

### <a name="system-versions"></a>Версии системы
 Можно использовать разные границы подсистемы , чтобы показать разные версии системы. Например, вариант использования оплаты может быть включен в веб-сайт версии 2, но не версии 1. Это означает, что система помогает клиентам осуществлять заказы. Однако клиенты должны оплачивать услуги ресторана напрямую.

 Use **Dependency** relations to link subsystems representing different versions or variants.

 ![Subsystems show different versions of a system](../modeling/media/uml-ucguidesystem.png "UML_UCGuideSystem")

## <a name="see-also"></a>См. также раздел
 [Model user requirements](../modeling/model-user-requirements.md) [UML Sequence Diagrams: Guidelines](../modeling/uml-sequence-diagrams-guidelines.md) [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md) [UML Use Case Diagrams: Reference](../modeling/uml-use-case-diagrams-reference.md) [UML Class Diagrams: Reference](../modeling/uml-class-diagrams-reference.md) [UML Component Diagrams: Reference](../modeling/uml-component-diagrams-reference.md) [UML Activity Diagrams: Guidelines](../modeling/uml-activity-diagrams-guidelines.md) [Video: Organizing Features into Use Cases](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-2-organizing-features-into-use-cases)
