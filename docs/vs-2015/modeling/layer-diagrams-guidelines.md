---
title: 'Layer Diagrams: Guidelines | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- architecture, layer diagrams
- layer diagrams
- diagrams - modeling, layer
- constraints, architectural
ms.assetid: 2903bec7-a93b-46a6-aac6-994ac4f3f1a7
caps.latest.revision: 57
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 51cb71d4bc2f66377b677d5be292c4eafa1dbd18
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299464"
---
# <a name="layer-diagrams-guidelines"></a>Схемы слоев: рекомендации
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Describe your app's architecture at a high level by creating *layer diagrams* in Visual Studio. Чтобы убедиться в том, что код соответствует этой структуре, проверьте его с помощью схемы слоев. В процесс сборки также можно включить проверку слоев. See [Channel 9 Video: Design and validate your architecture using layer diagrams](https://go.microsoft.com/fwlink/?LinkID=252073).

 Чтобы узнать, какие версии Visual Studio поддерживают эту функцию, см. раздел [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="what-is-a-layer-diagram"></a>Что такое схема слоев?
 Как и в традиционной схеме архитектуры, схема слоев определяет основные компоненты или функциональные единицы разработки, а также их взаимозависимости. Each node on the diagram, called a *layer*, represents a logical group of namespaces, projects, or other artifacts. Можно нарисовать зависимости для своей разработки. В отличие от традиционной схемы архитектуры, можно проверить, соответствуют ли действительные зависимости заданным вами предполагаемым зависимостям. Делая проверку частью стандартного построения в [!INCLUDE[esprtfs](../includes/esprtfs-md.md)], можно добиться того, чтобы программный код продолжал придерживаться архитектуры системы при дальнейших изменениях. See [Layer Diagrams: Reference](../modeling/layer-diagrams-reference.md).

## <a name="Update"></a> How to design or update your app with layer diagrams
 Следующие шаги показывают как использовать схемы слоев при разработке. Каждый шаг более подробно описан в последующих подразделах данного раздела. Если ведется разработка нового проекта, можно пропустить шаги, которые относятся к существующему коду.

> [!NOTE]
> Эти шаги приведены в примерном порядке. Возможно, понадобится перекрыть задачи, заново упорядочить их, чтобы они подходили по ситуации, а также возвратиться к ним в начале каждой итерации в проекте.

1. [Create a layer diagram](#Create) for the whole application, or for a layer within it.

2. [Define layers to represent primary functional areas or components](#CreateLayers) of your application. Дайте этим слоям имена согласно их функциям, например "Презентация" или "Службы". If you have a [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] solution, you can associate each layer with a collection of *artifacts*, such as projects, namespaces, files, and so on.

3. [Discover the existing dependencies](#Generate) between layers.

4. [Edit the layers and dependencies](#EditArchitecture) to show the updated design that you want the code to reflect.

5. [Design new areas of your application](#NewAreas) by creating layers to represent the principal architectural blocks or components and defining dependencies to show how each layer uses the others.

6. [Edit the layout and appearance of the diagram](#EditLayout) to help you discuss it with colleagues.

7. [Validate the code against the layer diagram](#Validate) to highlight the conflicts between the code and the architecture you require.

8. [Update the code to conform to your new architecture](#UpdateCode). Итерационно разрабатывайте и оптимизируйте код до тех пор, пока проверка не укажет, что конфликты отсутствуют.

9. [Include layer validation in the build process](#BuildValidation) to ensure that the code continues to adhere to your design.

## <a name="Create"></a> Create a layer diagram
 Схема слоев должна создаваться внутри проекта моделирования. Можно добавить новую схему слоя в существующий проект моделирования, создайте новый проект моделирования для схемы слоя или скопируйте схему слоя в том же проекте моделирования.

> [!IMPORTANT]
> Не следует добавлять, перетаскивать или копировать существующую схему слоев из одного проекта моделирования в другой или в другое местоположение в решении. Скопированные таким образом схемы слоев содержат те же ссылки, что и исходная схема, даже если вы ее измените. Это может привести к тому, что проверка схемы будет работать неправильно, а также к другим потенциальным проблемам, таким как отсутствующие элементы или другие ошибки при попытке открыть схему.

 See [Create layer diagrams from your code](../modeling/create-layer-diagrams-from-your-code.md).

## <a name="CreateLayers"></a> Define layers to represent functional areas or components
 Layers represent logical groups of *artifacts*, such as projects, code files, namespaces, classes, and methods. Можно создать слои из артефактов из проектов Visual C# .NET и Visual Basic .NET, или же можно привязать спецификации или планы к слою путем связывания документов, таких как файлы Word или презентации PowerPoint. Каждый слой представляет собой прямоугольник на схеме и показывает количество артефактов, связанных с ним. Слой может содержать вложенные слои, описывающие более конкретные задачи.

 Рекомендуется называть слои согласно их функциям, например "Презентация" или "Службы". Если артефакты тесно взаимосвязаны, поместите их в один слой. Если артефакты могут быть обновлены отдельно или использованы в разных приложениях, поместите их на разные слои. To learn about layering patterns, visit the Patterns & Practices site at [http://go.microsoft.com/fwlink/?LinkId=145794](https://go.microsoft.com/fwlink/?LinkId=145794).

> [!TIP]
> Существуют некоторые типы артефактов, которые можно связать со слоями, но при этом поддержки проверки схемы слоев не будет. To see whether the artifact supports validation, open **Layer Explorer** to examine the **Supports Validation** property of the artifact link. See [Discover existing dependencies between layers](#Generate).

 При обновлении незнакомого приложения можно также создать карты кода. Они помогают обнаружить закономерности и зависимости при анализе кода. Воспользуйтесь обозревателем решений, чтобы изучить пространства имен и классы, которые часто находятся в точном соответствии с существующими слоями. Назначьте эти артефакты кода слоям, перетащив их из обозревателя решений на схемы слоев. Затем схемы слоев можно использовать для обновления кода и обеспечения его соответствия проекту.

 Пример

- [Создание схем слоев на основе кода](../modeling/create-layer-diagrams-from-your-code.md)

- [Использование карт кода для отладки приложений](../modeling/use-code-maps-to-debug-your-applications.md)

- [Сопоставление зависимостей во всех решениях](../modeling/map-dependencies-across-your-solutions.md)

## <a name="Generate"></a> Discover existing dependencies between layers
 Зависимости существуют там, где артефакт, связанный с одним слоем, ссылается на артефакт, связанный с другим слоем. Например, класс в одном слое объявляет переменную, которая имеет класс в другом слое. Существующие зависимости можно обнаружить путем их реконструирования.

> [!NOTE]
> Для определенных видов артефактов реконструировать зависимости невозможно. Например, зависимости не могут быть реконструированы из или в слой, связанный с текстовым файлом. To see which artifacts have dependencies that you can reverse-engineer, right-click one or multiple layers, and then click **View Links**. In **Layer Explorer**, examine the **Supports Validation** column. Dependencies will not be reverse-engineered for artifacts for which this column shows **False**.

#### <a name="to-reverse-engineer-existing-dependencies-between-layers"></a>Чтобы выполнить реконструирование существующих зависимостей между слоями

- Select one layer or multiple layers, right-click a selected layer, and then click **Generate Dependencies**.

  Как правило, на этом этапе можно увидеть некоторые зависимости, которых быть не должно. Эти зависимости можно изменить для соответствия предполагаемой структуре.

## <a name="EditArchitecture"></a> Edit layers and dependencies to show the intended design
 Чтобы описать изменения, которые планируется внести в систему или предполагаемую архитектуру, осуществите следующие шаги для изменения схемы слоев. Можно также сделать некоторые оптимизационные изменения для улучшения структуры кода перед его расширением. See [Improving the structure of the code](#Improving).

|**Задача**|**Perform these steps**|
|------------|-----------------------------|
|Удаление зависимости, которой не должно существовать|Click the dependency, and then press **DELETE**.|
|Изменить или ограничить направление зависимости|Set its **Direction** property.|
|Создать новые зависимости|Use the **Dependency** and **Bidirectional Dependency** tools.<br /><br /> Чтобы нарисовать несколько зависимостей, дважды щелкните средство. When you are finished, click the **Pointer** tool or press the **ESC** key.|
|Указание, что артефакт, связанный со слоем, не может зависеть от указанного пространства имен|Type the namespaces in the layer's **Forbidden Namespace Dependencies** property. Use a semicolon ( **;** ) to separate the namespaces.|
|Указание, что артефакт, связанный со слоем, не должен более принадлежать указанному пространству имен|Type the namespaces in the layer's **Forbidden Namespaces** property. Use a semicolon ( **;** ) to separate the namespaces.|
|Указание, что артефакт, связанный со слоем, должен принадлежать одному из указанных пространств имен|Type the namespace in the layer's **Required Namespaces** property. Use a semicolon ( **;** ) to separate the namespaces.|

### <a name="Improving"></a> Improving the structure of the code
 Оптимизация изменений — это улучшения, которые не влияют на поведение приложения, но помогают сделать код более легким для изменения или расширения в будущем. Хорошо структурированный код имеет такой вид, который потом легко можно поместить в схему слоев.

 Например, если создается слой для каждого пространства имен в коде и затем разбираются зависимости, то необходимо, чтобы был минимальный набор односторонних зависимостей между слоями. Если создается более детальная схема с использованием классов или методов в качестве слоев, то результат должен иметь такие же характеристики.

 Если это не так, то код будет более сложным для изменения в течение всего времени и менее подходящим для проверки с использованием схем слоев.

## <a name="NewAreas"></a> Design new areas of your application
 При начале разработки нового проекта или новой области в новом проекте, можно нарисовать слои и зависимости, чтобы облегчить определение основных компонентов перед началом разработки кода.

- **Show identifiable architectural patterns** in your layer diagrams, if possible. Например, схема слоев, которая описывает настольное приложение, может включать такие слои, как "Презентация", "Доменная логика" и "Хранилище данных". Схема слоев, которая относится к одному компоненту приложения, может иметь такие слои, как "Модель", "Вид" и "Контроллер". For more information about such patterns, see [Patterns & Practices: Application Architecture](https://go.microsoft.com/fwlink/?LinkId=145794).

     Если вы часто создаете похожие шаблоны, то можно создать пользовательский инструмент. See [Define a custom modeling toolbox item](../modeling/define-a-custom-modeling-toolbox-item.md).

- **Create a code artifact for each layer** such as a namespace, class, or component. Это облегчит отслеживание кода и поможет связывать артефакты кода со слоями. Сразу после создания артефакта свяжите его с соответствующим слоем.

- **You do not have to link most classes and other artifacts to layers** because they fall within larger artifacts such as namespaces that you have already linked to layers.

- **Create a new diagram for a new feature**. Обычно будет создана одна или несколько схем слоев, описывающих все приложение. Если вы разрабатываете новую возможность в приложении, то не добавляйте и не изменяйте существующие схемы. Вместо этого создайте свою схему, которая отражает новые части кода. Слои в новой схеме могут включать в себя презентацию, доменную логику и слои базы данных для новой возможности.

     При построении приложения код будет проверяться как в отношении всей схемы , так и в отношении более детальной схемы возможности.

## <a name="EditLayout"></a> Edit the layout for presentation and discussion
 Чтобы облегчить определение слоев и зависимостей или обсудить их с членами команды, измените вид и разметку схемы следующим образом.

- Измените размеры, формы и положение слоев.

- Измените цвета слоев и зависимостей.

  - Select one or more layers or dependencies, right-click, and then click **Properties**. In the **Properties** window, edit the **Color** property.

## <a name="Validate"></a> Validate the code against the diagram
 После изменения схемы можно проверить код вручную в любое время или автоматически при каждом запуске локального построения или [!INCLUDE[esprbuild](../includes/esprbuild-md.md)].

 Пример

- [Проверка кода по схемам слоев](../modeling/validate-code-with-layer-diagrams.md)

- [Include Layer Validation in the Build Process](#BuildValidation)

## <a name="UpdateCode"></a> Update the code to conform to the new architecture
 Обычно ошибки появляются при первой проверке кода в обновленной схеме слоя. Ошибки могут возникать вследствие нескольких причин.

- Артефакт назначен неправильному слою. В этом случае следует переместить артефакт.

- Способ использования артефактом (например, классом) другого класса конфликтует с имеющейся архитектурой. В этом случае необходимо выполнить рефакторинг кода, чтобы устранить зависимость.

  Для устранения этих ошибок следует обновлять код до тех пор, пока в процессе проверки не перестанут происходить ошибки. Обычно это итерационный процесс. For more information about these errors, see [Validate code with layer diagrams](../modeling/validate-code-with-layer-diagrams.md).

> [!NOTE]
> Возможно, во время разработки или оптимизации кода понадобится связать новые артефакты со схемой слоев. Однако это может не потребоваться, например, когда слои представляют собой существующие пространства имен, а новый код только добавляет больше материала для них.

 В процессе разработки может понадобиться подавить некоторые конфликты, выявленные в ходе проверки. Например, можно подавлять ошибки, над которыми уже ведется работа, а также ошибки, не имеющие отношения к конкретному сценарию. При подавлении ошибки рекомендуется фиксировать рабочий элемент в журнале в [!INCLUDE[esprfound](../includes/esprfound-md.md)]. To perform this task, see [Validate code with layer diagrams](../modeling/validate-code-with-layer-diagrams.md).

## <a name="BuildValidation"></a> Include layer validation in the build process
 Чтобы убедиться, что будущие изменения в коде соответствуют схеме слоев, включите проверку слоев в стандартный процесс построения решения. Всякий раз, когда другая команда начинает построение решения, любые изменения между зависимостями в коде и в схеме слоев будут отображаться как ошибки построения. For more information about including layer validation in the build process, see [Validate code with layer diagrams](../modeling/validate-code-with-layer-diagrams.md).

## <a name="see-also"></a>См. также раздел
 [Layer Diagrams: Reference](../modeling/layer-diagrams-reference.md) [Create layer diagrams from your code](../modeling/create-layer-diagrams-from-your-code.md)
