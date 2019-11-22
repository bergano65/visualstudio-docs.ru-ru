---
title: Edit UML models and diagrams | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.modelingproject
- vs.teamarch.UMLModelExplorer
- vs.teamarch.UMLModelExplorer.rootnode
helpviewer_keywords:
- diagrams - modeling
- UML, copy and paste
- UML, models
- UML model
- UML, element properties
- UML
- UML, diagrams
ms.assetid: 87affd40-8127-4ee9-9d3a-ad977abe2ed6
caps.latest.revision: 86
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 00ac30cc7e9ee3aff0dd64f015a4b4954972c09a
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295524"
---
# <a name="edit-uml-models-and-diagrams"></a>Изменение моделей и схем UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Модель UML можно создавать и изменять с помощью представлений, предоставляемых несколькими разными типами схем. Представляя различные точки зрения на систему, эти схемы помогают понять и обсудить различные аспекты ее разработки и требований к ней. Visual Studio предоставляет шаблоны для пяти наиболее часто используемых типов схем UML.

 Чтобы узнать, какие версии Visual Studio поддерживают эту функцию, см. раздел [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 В этом разделе описываются способы редактирования модели, общие для различных типов схем. For more information that is specific to particular types of diagrams, see [Create models for your app](../modeling/create-models-for-your-app.md).

## <a name="in-this-topic"></a>В этом разделе

- [UML Diagrams are Views of a UML Model](#Views)

- [Creating UML Modeling Diagrams](#Creating)

- [Drawing UML Modeling Diagrams](#Drawing)

- [Editing Shapes and Connectors](#Editing)

- [Undoing Changes to the Model](#Undo)

- [Sharing Elements between Diagrams](#Sharing)

- [Copying Elements and Groups of Related Elements](#Copying)

- [Deleting a Model Element or its Views](#Deleting)

- [Searching text in a diagram](#Searching)

- [Preparing a Diagram for Presentation](#presentation)

- [Extending the UML Designers](#extensions)

## <a name="Views"></a> UML Diagrams are Views of a UML Model
 Схемы UML можно создавать и использовать только в проектах моделирования. For more information about how to create diagrams and projects, see [Create UML modeling projects and diagrams](../modeling/create-uml-modeling-projects-and-diagrams.md).

- Проект моделирования содержит одну модель UML. Все схемы UML в проекте является представлением модели UML.

- You can see the model in **UML Model Explorer**. On the **Architecture** menu, point to **Windows**, and then click **UML Model Explorer**.

- Каждая фигура на схеме является представлением элемента в модели. При размещении новой фигуры на схеме вы создаете новый элемент в модели.

- When you save any diagram, Visual Studio saves the whole model, all its diagrams, and the modeling project file.

## <a name="Creating"></a> Creating UML Modeling Diagrams

1. On the **Architecture** menu in Visual Studio, click **New UML or Layer Diagram**.

2. Выберите схему и присвойте ей имя.

3. In **Add to modeling project**, select an existing modeling project, or select **Create a new modeling project**.

   > [!NOTE]
   > Схема моделирования должна существовать внутри проекта моделирования.

   Можно также добавить схему в существующий проект моделирования в обозревателе решений. Right-click the modeling project, point to **Add**, and then click **New Item**.

#### <a name="to-create-an-empty-uml-modeling-project"></a>Создание пустого проекта моделирования UML

- On the **File** menu, point to **New**, click **Project**, and in the **New Project** dialog box, double-click **Modeling Projects**.

  For more information about how to manage modeling projects, see [Create UML modeling projects and diagrams](../modeling/create-uml-modeling-projects-and-diagrams.md).

## <a name="Drawing"></a> Drawing UML Modeling Diagrams
 Схема моделирования отображает коллекцию элементов модели, связанных отношениями. Каждый элемент отображается в виде фигуры, а каждое отношение отображается в виде соединителя между двумя фигурами.

 Существует два вида инструментов: для элементов и для отношений. For example, in the UML class diagram Toolbox, **Class** is an element tool, and **Association** is a relationship tool.

> [!NOTE]
> If you want information that is specific to particular diagram types, see [Create models for your app](../modeling/create-models-for-your-app.md).

#### <a name="to-create-elements-and-relationships-in-a-uml-modeling-diagram"></a>Создание элементов и отношений в схеме моделирования UML

1. Чтобы создать элемент модели, щелкните инструмент элемента на панели элементов и выберите схему, где его требуется отобразить. После создания элемента измените его размер и форму, перетаскивая маркеры.

    В некоторых случаях можно поместить новый элемент внутрь другого элемента. Например, на схеме классов UML можно поместить класс внутрь пакета.

   > [!NOTE]
   > If you cannot see the toolbox, click **Toolbox** on the **View** menu.

2. Чтобы создать отношение, щелкните инструмент отношений, выберите элемент, с которого должно начинаться отношение, и выберите конечный элемент отношения.

    Различные типы отношений могут начинаться и заканчиваться разными типами элементов. Например, на схеме классов UML отношение ассоциации не может начинаться или заканчиваться элементом комментария.

   > [!NOTE]
   > Чтобы использовать один инструмент несколько раз, дважды щелкните его. When you have finished, click the **Pointer** tool.

   На некоторых типах схем можно рисовать простые фигуры. Эти фигуры не являются частью модели, но их можно использовать для привлечения внимания к частям схемы или для разделения ее на различные области.

## <a name="Editing"></a> Editing Shapes and Connectors
 В случае изменения размера или цвета фигуры или изменения маршрута соединителя это никак не повлияет на базовую модель. Однако при переименовании фигуры на схеме или в обозревателе моделей UML соответствующий элемент переименовывается в обозревателе моделей UML и на всех других схемах, содержащих этот элемент.

> [!NOTE]
> Существует простой способ создавать новые элементы панели элементов, из которых можно формировать группы элементов, или элементы с собственным набором свойств. For more information, see [Define a custom modeling toolbox item](../modeling/define-a-custom-modeling-toolbox-item.md).

 На следующем рисунке показано, как изменить размер фигуры или ее имя.

 ![Adjusting a model element](../modeling/media/uml-drawadjust1.png "UML_DrawAdjust1")

> [!TIP]
> В число встроенных команд не входит команда для аккуратного выравнивания фигур. However, you can easily create your own alignment command by copying the code in the example in [Display a UML model on diagrams](../modeling/display-a-uml-model-on-diagrams.md).

 На следующем рисунке показано, как настроить маршрут и положение соединителя или его меток.

 ![Adjusting a connector](../modeling/media/uml-drawadjust2.png "UML_DrawAdjust2")

#### <a name="to-move-one-end-of-a-connector-to-another-shape"></a>Перемещение одного конца соединителя на другую фигуру

1. Выполните одно из следующих действий.

   - Press **CTRL** and move the end.

     \- или -

   - Right-click the connector and then click **Reconnect**.

2. Щелкните конец соединителя, который требуется переместить.

3. Щелкните фигуру, на которую требуется переместить соединитель.

#### <a name="to-change-color-or-other-properties-of-an-element-relationship-or-diagram"></a>Изменение цвета или других свойств элемента, отношения или схемы

- Click the element and set the fields in the **Properties** window.

     If you cannot see the **Properties** window, right-click the element, and then click **Properties.**

#### <a name="to-zoom-in-and-out-on-a-modeling-diagram"></a>Увеличение и уменьшение масштаба схемы моделирования

- Press and hold the **CTRL** key while you rotate the mouse wheel.

     \- или -

- Press and hold **CTRL+SHIFT**, and then click the left or right mouse button.

     \- или -

- On the **Architecture Designers** toolbar, click the plus sign ( **+** ) or minus sign ( **-** ), or choose a zoom level.

## <a name="Searching"></a> Searching in a Diagram
 Функция быстрого поиска позволяет искать элементы на схеме. You must set **Look in:** to **Current Document**.

#### <a name="to-search-for-text-in-a-modeling-diagram"></a>Поиск текста на схеме моделирования

1. Press **CTRL+F**.

     \- или -

     On the **Edit** menu, point to **Find and Replace**, and then click **Quick Find**.

    > [!NOTE]
    > In the **Find and Replace** dialog box, you must leave the **Look in** field set to **Current Document**. Другие значения не поддерживаются.

2. Type the text that you want to find, and then click **Find Next**.

    > [!NOTE]
    > Если текст, который требуется найти, находится внутри свернутой фигуры, эта фигура будет выделена. Expand the shape, and then click **Find Next** again.

## <a name="Undo"></a> Undoing Changes to the Model
 You can undo and redo changes that you have made to the model and diagrams by using the **Undo** and **Redo** commands on the **Edit** menu.

 **Each modeling project has a single stack of changes.** Все вносимые в модель и схемы изменения хранятся в этом стеке. Стек также включает в себя изменения фокуса с одной схемы на другую. Команда отмены отменяет изменения в этом стеке.

 Например, предположим, что выполняются следующие операции: изменение схемы 1, изменение фокуса на схему 2, изменение схемы 2. При отмене изменений первая команда отмены отменит последнее изменение, следующая вернет фокус на схему 1, а третья отменит изменение схемы 1.

 **Closing a diagram truncates the stack of changes.** В случае закрытия схемы нельзя отменить изменения, внесенные в эту схему, а также предыдущие изменения модели или любой ее схемы.

 **You cannot undo while you are editing a property.** При редактировании свойства в окне свойств или в метке на схеме можно отменить только изменения, внесенные в это свойство. Завершите изменение свойства нажатием клавиши ВВОД или отмените его, нажав клавишу ESC. После этого вы сможете отменить изменения в модели и схемах.

 **Closing a diagram without saving might not have the effect you expect.** Если внести некоторые изменения, а затем закрыть схему без сохранения, изменения все равно будут сохранены в модели. Рекомендуется закрывать всю модель, если вы хотите сделать это без сохранения.

## <a name="Sharing"></a> Sharing Elements between Diagrams
 Определенный экземпляр элемента модели можно отобразить на схемах несколько раз. Это относится к классам, интерфейсам, компонентам, вариантам использования и субъектам.

 Это удобно, если нужно показать различные группы отношений на разных схемах. Например, на одной схеме можно показать ассоциации между классами клиента и адреса. На другой схеме можно снова показать класс адреса, имеющий ассоциацию с почтовым районом.

 Свойства элемента модели, например его имя, можно изменить, выбрав любое из его представлений на любой схеме или выбрав его в обозревателе моделей UML.

 Каждый из типов схем может отображать только некоторые виды элементов модели. Например, нельзя отобразить вариант использования на схеме компонентов. Поэтому следующие процедуры будут работать только для определенных сочетаний схемы и элемента модели.

#### <a name="to-add-a-new-view-of-a-model-element-by-using-uml-model-explorer"></a>Добавление нового представления элемента модели с помощью обозревателя моделей UML

1. To open **UML Model Explorer**, on the **Architecture** menu, point to **Windows**, and then click **UML Model Explorer**.

2. Drag the model element from **UML Model Explorer** to a compatible diagram in the same project.

     Отображается фигура, предоставляющая представление элемента модели, что может служить дополнением представлений на других схемах или на той же самой схеме.

    > [!NOTE]
    > Иной результат дает перетаскивание класса или компонента на схему последовательностей. В этом случае создается новый жизненный цикл, типом которого является этот класс или компонент. For more information, see [UML Sequence Diagrams: Guidelines](../modeling/uml-sequence-diagrams-guidelines.md).

#### <a name="to-add-a-new-view-of-a-model-element-by-using-paste-reference"></a>Добавление нового представления элемента модели с помощью команды "Вставить ссылку"

1. Right-click an existing element, and then click **Copy**.

    - Можно скопировать несколько элементов за один раз. Hold down the CTRL key while you click each element, right-click one of them, and then click **Copy**.

2. Right-click an empty part of a compatible diagram, and then click **Paste Reference**.

     Появляется другое представление того же самого элемента.

    > [!NOTE]
    > This differs from the **Paste** command, which creates a new element in the model. For more information, see [Copying Elements and Groups of Related Elements](#Copying).

> [!NOTE]
> Если добавить в схему представления двух элементов модели, уже связанных отношением, представление этого отношения также отображается на схеме. В этом представлении можно удалить, только удалив один из элементов из схемы или удалив связь из модели.

## <a name="Copying"></a> Copying Elements and Groups of Related Elements
 Можно копировать и вставлять элементы модели, а также копировать и вставлять группы элементов вместе с отношениями между ними.

> [!NOTE]
> The **Paste** and **Paste Reference** commands have different effects. **Paste** creates new elements whose properties are like those of the copied elements. **Paste Reference** creates new views of the same elements.

#### <a name="to-copy-elements-and-their-relationships"></a>Копирование элементов и их отношений

1. На схеме с элементами, которые требуется скопировать, выберите один или несколько элементов.

    > [!NOTE]
    > Копировать отношения можно только в виде части группы элементов.

2. On the **Edit** menu, click **Copy**.

3. Если требуется скопировать элементы в другую схему, создайте новую схему или откройте существующую.

4. On the **Edit** menu, click **Paste**.

    - Отображаются копии элементов вместе с копиями связывающих их отношений.

    - Каждый новый элемент получает новое имя, создаваемое автоматически.

5. Настройте положения, имена и другие свойства новых элементов и отношений.

> [!NOTE]
> Нельзя скопировать элемент модели из одной модели в другую, например при наличии двух моделей в одном решении. Однако можно скопировать элементы с одной схемы в другую.

#### <a name="to-copy-an-entire-diagram"></a>Копирование всей схемы

1. Создайте новую схему.

2. Выберите все элементы на существующей схеме, скопируйте их и вставьте в новую схему.

   Нельзя реплицировать схему путем копирования и вставки в обозревателе решений.

## <a name="Deleting"></a> Deleting a Model Element or its Views
 Некоторые виды элементов, в частности классификаторы, можно удалить из схемы без удаления их из модели. Классификаторы — это основные элементы, которые отображаются на схемах классов, схемах компонентов и схемах вариантов использования. Они могут отображаться на нескольких схемах. For these types of elements, there are two separate commands: **Remove from Diagram** and **Delete from Model**.

 В противоположность этому при удалении отношения из схемы оно всегда удаляется и из модели.

> [!NOTE]
> Некоторые виды элементов на схеме UML имеют метки. Когда вы выбираете такие элементы, рисуя вокруг них прямоугольник, можно выбрать метки, но не элементы, которым они принадлежат. Удаление подмножества элементов, выбранных таким образом, не поддерживается. To select a subset of these elements, press and hold the **CTRL** key while you click each element.

#### <a name="to-remove-a-classifiers-view-from-a-diagram"></a>Удаление представления классификатора из схемы

- Right-click the element on the diagram, and then click **Remove from Diagram**.

  \- или -

- Click the element on the diagram and then press the **DELETE** key.

  - Это представление элемента удаляется. However, the element remains in the model, and you can still find it in **UML Model Explorer**. Все другие представления этого элемента также сохраняются.

  - Каждый соединитель, оканчивающийся на данной фигуре, удаляется из схемы, однако представленное им отношение остается в модели. You can see the relationship in **UML Model Explorer** under **Relationships**, under each element that it connects.

#### <a name="to-delete-an-element-from-the-model"></a>Удаление элемента из модели

- Right-click the element either in **UML Model Explorer** or on a diagram, and then click **Delete from Model**.

  - Элемент удаляется из всех схем, на которых он отображается.

  - Каждое отношение, которое заканчивается на этом элементе, также удаляется из модели.

#### <a name="to-delete-a-relationship-from-the-model"></a>Удаление отношения из модели

- Right-click the relationship on a diagram or in **UML Model Explorer**, and then click **Delete from Model**.

    > [!CAUTION]
    > Отношение нельзя удалить из схемы без его удаления из модели.

     Отношение удаляется из модели и удаляется из всех схем, на которых оно отображается.

## <a name="presentation"></a> Preparing a Diagram for Presentation
 Следующие функции помогают привлечь внимание к определенным частям схемы, добавить пояснения или разделить схему на различные области.

- Можно скопировать любую часть схемы в Word, PowerPoint или другой документ. Select the shapes and connectors you want, right-click and then click **Copy**.

- Можно изменить цвет любой фигуры или любого соединителя. Select one or more shapes and change the **Color** property. Если окно **Свойства** не отображается, нажмите клавишу **F4**.

- On diagrams of some kinds, you can draw lines, rectangles and ellipses from the **Simple Shapes** section of the Toolbox. Эти фигуры не являются частью модели UML.

- To label an area, you can drag a Comment from the Toolbox and then set its **Transparent** property to **True**. Как и простые фигуры, комментарии не являются частью модели UML и не отображаются в обозревателе моделей UML.

- Чтобы добавить заметки и пояснения к элементам модели, можно создать комментарии и связать их с этими элементами.

### <a name="to-export-a-diagram-as-an-image"></a>Экспорт схемы в виде изображения
 For more information, see [Export diagrams as images](../modeling/export-diagrams-as-images.md).

## <a name="extensions"></a> Extending the UML Designers
 Можно добавить новые функциональные возможности для инструментов UML и адаптировать нотацию схемы под свои потребности. For more information, see [Extend UML models and diagrams](../modeling/extend-uml-models-and-diagrams.md).

## <a name="see-also"></a>См. также раздел
 [Create UML modeling projects and diagrams](../modeling/create-uml-modeling-projects-and-diagrams.md) [Analyzing and Modeling Architecture](../modeling/analyze-and-model-your-architecture.md) [Create models for your app](../modeling/create-models-for-your-app.md)
