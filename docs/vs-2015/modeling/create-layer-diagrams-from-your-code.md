---
title: Create layer diagrams from your code | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- architecture, layer diagrams
- layer diagrams
- diagrams - modeling, layer
- constraints, architectural
ms.assetid: 58c3ea71-2dbc-4963-bf82-40f1924cf973
caps.latest.revision: 64
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3e6cd77e785adb59fc8b2cf3b28724ed0efe1ae3
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300270"
---
# <a name="create-layer-diagrams-from-your-code"></a>Создание схем слоев на основе кода
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

To visualize your software system's high-level, logical architecture, create a *layer diagram* in Visual Studio. Чтобы убедиться в том, что код соответствует этой структуре, проверьте его с помощью схемы слоев. Можно создать схемы слоев для проектов Visual C# .NET и Visual Basic .NET. To see which versions of Visual Studio support this feature, see [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)

 ![Create a layer diagram](../modeling/media/layerdiagramvisualizecode.png "LayerDiagramVisualizeCode")

 A layer diagram lets you organize Visual Studio solution items into logical, abstract groups called *layers*. Слои можно использовать для описания основных задач, выполняемых этими артефактами, или основных компонентов системы. Каждый слой может содержать другие слои, описывающие более подробные задачи. You can also specify the intended or existing *dependencies* between layers. Эти зависимости, представленные в виде стрелок, указывают, какие слои могут использовать или в настоящее время используют функциональные возможности, представленные другими слоями. Для поддержки архитектурного контроля кода добавьте предполагаемые зависимости в схему, а затем проверьте код по схеме.

## <a name="CreateDiagram"></a> Create a layer diagram
 Перед созданием схемы слоев решение должно иметь проект моделирования. See [Create UML modeling projects and diagrams](../modeling/create-uml-modeling-projects-and-diagrams.md).

> [!IMPORTANT]
> Не следует добавлять, перетаскивать или копировать существующую схему слоев из одного проекта моделирования в другой проект моделирования или в другое местоположение в решении. Это позволит сохранить ссылки из исходной схемы при изменении схемы. Кроме того, это может привести к тому, что проверка схемы будет работать неправильно, и к другим потенциальным проблемам, таким как отсутствующие элементы или другие ошибки при попытке открыть схему.
>
> Вместо этого добавьте новую схему слоев в проект моделирования. Скопируйте элементы из исходной схемы в новую схему. Сохраните оба проекта моделирования и новую схему слоев.

#### <a name="to-add-a-new-layer-diagram-to-a-modeling-project"></a>Добавление новой схемы слоев в проект моделирования

1. On the **Architecture** menu, choose **New UML or Layer Diagram**.

2. Under **Templates**, choose **Layer Diagram**.

3. Назовите схему.

4. In **Add to Modeling Project**, browse to and select an existing modeling project in your solution.

     \- или -

     Choose **Create a new modeling project** to add a new modeling project to the solution.

    > [!NOTE]
    > Схема слоя должна существовать внутри проекта моделирования. Однако ее можно связать с элементами в любом месте решения.

5. Убедитесь, что сохранены оба проекта моделирования и схема слоев.

## <a name="CreateLayers"></a> Create layers from artifacts
 Слои можно создать из элементов решения Visual Studio, таких как проекты, файлы кода, пространства имен, классы и методы. При этом автоматически создаются связи между слоями и элементами, которые включаются в процесс проверки слоев.

 Слои также можно связывать с элементами, которые не поддерживают проверку, такими как документы Word или презентации PowerPoint, чтобы можно было связать слой со спецификациями или планами. Кроме того, слои можно связать с файлами в проектах, которые являются общими для нескольких приложений, но в процесс проверки не войдут слои, которые отображаются с универсальными именами, например "Уровень 1" и "Уровень 2".

 To see if a linked item supports validation, open **Layer Explorer** and examine the **Supports Validation** property of the item. See [Managing links to artifacts](#Managing).

|**Задача**|**Follow these steps**|
|------------|----------------------------|
|Создать слой для одного артефакта|<ol><li>Перетащите элемент на схему слоев из указанных ниже источников.<br /><br /> <ul><li>**Обозреватель решений**<br /><br />         Например, можно перетаскивать файлы или проекты.</li><li>Карты кода<br /><br />         See [Map dependencies across your solutions](../modeling/map-dependencies-across-your-solutions.md) and [Use code maps to debug your applications](../modeling/use-code-maps-to-debug-your-applications.md).</li><li>**Class View** or **Object Browser**</li></ul><br />     Слой отображается на схеме и связан с артефактом.</li><li>Переименуйте слой, чтобы отразить обязанности связанного кода или артефактов.</li></ol> **Important:**  Dragging binary files to the layer diagram does not automatically add their references to modeling project. Необходимо вручную добавить двоичные файлы, которые нужно проверить, в проект моделирования. **To add binary files to the modeling project** <ol><li>In **Solution Explorer**, open the shortcut menu for the modeling project, and then choose **Add Existing Item**.</li><li>In the **Add Existing Item** dialog box, browse to the binary files, select them, and then choose **OK**.     Двоичные файлы отображаются в проекте моделирования.</li><li>In **Solution Explorer**, choose a binary file that you added, and then press **F4** to open the **Properties** window.</li><li>On each binary file, set the **Build Action** property to **Validate**.</li></ol>|
|Создание единственного слоя для всех выбранных артефактов|Одновременно перетащите на схему слоев все артефакты.<br /><br /> Слой отображается в схеме и связан со всеми артефактами.|
|Создание слоя для каждого выбранного артефакта|Press and hold the **SHIFT** key while you drag all of the artifacts to the layer diagram at the same time. **Note:**  If you use the **SHIFT** key to select a range of items, release the key after you select the artifacts. Нажмите и удерживайте ее снова при перетаскивании артефактов в схему. <br /><br /> Слой для каждого артефакта отображается в схеме и связан с каждым артефактом.|
|Добавление артефакта в слой|Перетащите артефакт в слой.|
|Создание нового несвязанного слоя|In the **Toolbox**, expand the **Layer Diagram** section, and then drag a **Layer** to the layer diagram.<br /><br /> Чтобы добавить несколько слоев, дважды щелкните средство. When you are finished, choose the **Pointer** tool or press the **ESC** key.<br /><br /> -или-<br /><br /> Open the shortcut menu for the layer diagram, choose **Add**, and then choose **Layer**.|
|Создание вложенных слоев|Перетащите существующий слой в другой слой.<br /><br /> -или-<br /><br /> Open the shortcut menu for a layer, choose **Add**, and then choose **Layer**.|
|Создание нового слоя, который содержит два или более существующих слоев|Select the layers, open the shortcut menu for your selection, and then choose **Group**.|
|Изменение цвета слоя|Set its **Color** property to the color that you want.|
|Указание, что артефакт, связанный со слоем, не должен более принадлежать указанному пространству имен|Type the namespaces in the layer's **Forbidden Namespaces** property. Use a semicolon ( **;** ) to separate the namespaces.|
|Указание, что артефакт, связанный со слоем, не может зависеть от указанного пространства имен|Type the namespaces in the layer's **Forbidden Namespace Dependencies** property. Use a semicolon ( **;** ) to separate the namespaces.|
|Указание, что артефакт, связанный со слоем, должен принадлежать одному из указанных пространств имен|Type the namespace in the layer's **Required Namespaces** property. Use a semicolon ( **;** ) to separate the namespaces.|

 Число на слое обозначает количество артефактов, связанных со слоем. Однако при считывании этого числа учитывайте следующее.

- Если слой связан с артефактом, содержащим другие артефакты, но слой не связан с другими артефактами напрямую, то число включает только связанный артефакт. Однако для анализа в ходе проверки слоя включаются другие артефакты.

     Например, если слой связан с одним пространством имен, то число связанных артефактов равно 1, даже если пространство имен содержит классы. Если слой также связан с каждым классом в пространстве имен, то число будет включать эти связанные классы.

- Если слой содержит другие слои, связанные с артефактами, то слой-контейнер также связан с этими артефактами, даже если число в слое-контейнере не включает эти артефакты.

## <a name="Managing"></a> Manage links between layers and artifacts

1. On the layer diagram, open the shortcut menu for the layer, and then choose **View Links**.

     **Layer Explorer** shows the artifact links for the selected layer.

2. Для управления этими ссылками можно использовать следующие задачи:

|**Задача**|**In Layer Explorer**|
|------------|---------------------------|
|Удалить ссылку между слоем и артефактом|Open the shortcut menu for the artifact link, and then choose **Delete**.|
|Переместить ссылку из одного слоя в другой|Перетащите ссылку артефакта в существующий слой на схеме.<br /><br /> -или-<br /><br /> 1.  Open the shortcut menu for the artifact link, and then choose **Cut**.<br />2.  On the layer diagram, open the shortcut menu for the layer, and then choose **Paste**.|
|Скопировать ссылку из одного слоя в другой|1.  Open the shortcut menu for the artifact link, and then choose **Copy**.<br />2.  On the layer diagram, open the shortcut menu for the layer, and then choose **Paste**.|
|Создать новый слой из существующей ссылки артефакта|Перетащите ссылку артефакта в пустую область на схеме.|
|Убедитесь, что связанный артефакт поддерживает проверку относительно схемы слоев.|Look at the **Supports Validation** column for the artifact link.|

## <a name="Discovering"></a> Reverse-engineer existing dependencies
 Зависимости существуют там, где артефакт, связанный с одним слоем, ссылается на артефакт, связанный с другим слоем. Например, класс в одном слое объявляет переменную, которая имеет класс в другом слое. Реконструировать существующие зависимости можно для артефактов, связанных со слоями в схеме.

> [!NOTE]
> Для определенных видов артефактов реконструировать зависимости невозможно. Например, зависимости не могут быть реконструированы из или в слой, связанный с текстовым файлом. To see which artifacts have dependencies that you can reverse-engineer, open the shortcut menu for one or multiple layers, and then choose **View Links**. In **Layer Explorer**, examine the **Supports Validation** column. Dependencies will not be reverse-engineered for artifacts for which this column shows **False**.

- Select one or multiple layers, open the shortcut menu for a selected layer, and then choose **Generate Dependencies**.

  Как правило, на этом этапе можно увидеть некоторые зависимости, которых быть не должно. Эти зависимости можно изменить для соответствия предполагаемой структуре.

## <a name="EditDependencies"></a> Edit layers and dependencies to show the intended design
 Чтобы описать изменения, которые планируется внести в систему или предполагаемую архитектуру, измените схему слоев.

|**Задача**|**Perform these steps**|
|------------|-----------------------------|
|Изменить или ограничить направление зависимости|Set its **Direction** property.|
|Создать новые зависимости|Use the **Dependency** and **Bidirectional Dependency** tools.<br /><br /> Чтобы нарисовать несколько зависимостей, дважды щелкните средство. When you are finished, choose the **Pointer** tool or press the **ESC** key.|
|Указание, что артефакт, связанный со слоем, не может зависеть от указанного пространства имен|Type the namespaces in the layer's **Forbidden Namespace Dependencies** property. Use a semicolon ( **;** ) to separate the namespaces.|
|Указание, что артефакт, связанный со слоем, не должен более принадлежать указанному пространству имен|Type the namespaces in the layer's **Forbidden Namespaces** property. Use a semicolon ( **;** ) to separate the namespaces.|
|Указание, что артефакт, связанный со слоем, должен принадлежать одному из указанных пространств имен|Type the namespace in the layer's **Required Namespaces** property. Use a semicolon ( **;** ) to separate the namespaces.|

## <a name="EditLayout"></a> Change how elements appear on the diagram
 Можно изменить размер, фигуру, цвет, положение слоев или цвет зависимостей, изменив их свойства.

## <a name="Codemaps"></a> Discover patterns and dependencies on a code map
 While creating layer diagrams, you might also create **code maps**. Они помогают обнаружить закономерности и зависимости при анализе кода. Воспользуйтесь обозревателем решений, представлением классов или обозревателем объектов, чтобы изучить сборки, пространства имен и классы, которые часто находятся в точном соответствии с существующими слоями. Подробнее о картах кода читайте в следующих разделах:

- [Сопоставление зависимостей во всех решениях](../modeling/map-dependencies-across-your-solutions.md)

- [Использование карт кода для отладки приложений](../modeling/use-code-maps-to-debug-your-applications.md)

- [Поиск потенциальных проблем с помощью анализаторов карт кода](../modeling/find-potential-problems-using-code-map-analyzers.md)

## <a name="see-also"></a>См. также раздел
 [Channel 9 Video: Design and validate your architecture using layer diagrams](https://go.microsoft.com/fwlink/?LinkID=252073) [Layer Diagrams: Reference](../modeling/layer-diagrams-reference.md) [Layer Diagrams: Guidelines](../modeling/layer-diagrams-guidelines.md) [Validate code with layer diagrams](../modeling/validate-code-with-layer-diagrams.md) [Visualize code](../modeling/visualize-code.md)