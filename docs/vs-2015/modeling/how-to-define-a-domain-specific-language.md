---
title: How to Define a Domain-Specific Language | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.domainrelationship
- vs.dsltools.dsldesigner.domainclass
- vs.dsltools.dsldesigner.domaintype
helpviewer_keywords:
- Domain-Specific Language, domain class
- Domain-Specific Language, external types
- Domain-Specific Language, relationships
- Domain-Specific Language, domain properties
ms.assetid: d1772463-0eb1-40a5-b7c0-9a008bc76760
caps.latest.revision: 45
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b4bcd1f1f023c9e439fb870c9e31f07aa5be215d
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299549"
---
# <a name="how-to-define-a-domain-specific-language"></a>Определение доменного языка
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Чтобы определить доменный язык (DSL), необходимо создать решение [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] из шаблона. Ключевой частью решения является схема определения DSL, которая хранится в файле DslDefinition.dsl. Определение DSL определяет классы и фигуры DSL. После внесения изменений и добавления элементов можно добавить программный код для более детальной настройки DSL.

 If you are new to DSLs, we recommend that you work through the **DSL Tools Lab**, which you can find in this site: [Visualizaton and Modeling SDK](https://go.microsoft.com/fwlink/?LinkID=186128)

## <a name="templates"></a> Selecting a Template Solution
 Для определения доменного языка необходимо установить следующие компоненты.

|||
|-|-|
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185579](https://go.microsoft.com/fwlink/?LinkId=185579)|
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185580](https://go.microsoft.com/fwlink/?LinkId=185580)|
|Пакет SDK для визуализации и моделирования в Visual Studio|[http://go.microsoft.com/fwlink/?LinkID=186128](https://go.microsoft.com/fwlink/?LinkID=186128)|

 Для создания нового доменного языка необходимо создать новое решение [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] при помощи шаблона проекта доменного языка.

#### <a name="to-create-a-dsl-solution"></a>Создание решения DSL

1. Create a solution with the **Domain-Specific Language** template, which can be found under **Other Project Types/Extensibility** in the **New Project** dialog box.

    ![Create DSL dialog](../modeling/media/create-dsldialog.png "Create_DSLDialog")

    When you click **OK**, the **Domain-Specific Language Wizard** opens and displays a list of template DSL solutions.

2. Нажмите на каждый шаблон, чтобы увидеть его описание. Выберите решение, максимально соответствующее тому, что вы хотите создать.

    Каждый шаблон DSL определяет основной рабочий DSL. Этот DSL можно отредактировать в соответствии с вашими требованиями.

    Нажмите на каждый образец, чтобы получить дополнительную информацию.

   - Select **Task Flow** to create a DSL that has swimlanes. Дорожки — это вертикальные или горизонтальные разделы схемы.

   - Select **Component Models** to create a DSL that has ports. Порты — это небольшие фигуры на краю более крупной фигуры.

   - Select **Class Diagrams** to define a DSL that has compartment shapes. Фрагменты фигур содержат списки элементов.

   - Select **Minimal Language** in other cases, or if you are uncertain.

       > [!NOTE]
       > Если требуется создать схему классов или компонентов, лучше всего использовать модели UML. Средства моделирования UML предоставляют набор схем, собранных в единую модель. Они могут расширяться и интегрироваться в DSL при помощи ModelBus. For more information, see [Create models for your app](../modeling/create-models-for-your-app.md).

   - Select **Minimal WinForm Designer** or **Minimal WPF Designer** to create a DSL that is displayed on a Windows Forms or WPF surface. Вам нужно будет написать код для определения редактора. Дополнительные сведения см. в следующих разделах:

        [Создание доменного языка на основе Windows Forms](../modeling/creating-a-windows-forms-based-domain-specific-language.md)

        [Создание доменного языка на основе WPF](../modeling/creating-a-wpf-based-domain-specific-language.md)

3. Введите расширение имени файла для DSL на соответствующей странице мастера. Это расширение будут использовать файлы, содержащие экземпляры DSL.

   - Выберите расширение имени файла, не связанное ни с одним другим приложением на вашем или другом компьютере, где планируется устанавливать DSL. For example, **docx** and **htm** would be unacceptable file name extensions.

   - Мастер предупредит, если расширение уже используется в качестве DSL. В этом случае выберите другое расширение имени файла. Можно также сбросить экземпляр экспериментального пакета SDK для Visual Studio, чтобы удалить старые экспериментальные конструкторы. Click **Start**, click **All Programs**, **Microsoft Visual Studio 2010 SDK**, **Tools**, and then **Reset the Microsoft Visual Studio 2010 Experimental instance**.

4. Также можно изменить настройки на других страницах или оставить значения по умолчанию.

5. Нажмите кнопку **Готово**.

    Мастер создаст решение, содержащее два или три проекта, и сгенерирует код из определения DSL.

   После этого пользовательский интерфейс примет следующий вид:

   ![конструктор dsl](../modeling/media/dsl-designer.png "dsl_designer")

   Данное решение определяет доменный язык. For more information, see [Overview of the Domain-Specific Language Tools User Interface](../modeling/overview-of-the-domain-specific-language-tools-user-interface.md).

### <a name="test-the-solution"></a>Тестирование решения
 Шаблон решения предоставляет рабочий DSL, который можно изменить или использовать как есть.

 Чтобы протестировать решение нажмите клавишу F5 или комбинацию клавиш CTRL + F5. Новый экземпляр [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] откроется в экспериментальном режиме.

 В новом экземпляре [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] в Обозревателе решений откройте файл Sample. Он откроется в виде схемы с панелью элементов.

 If you run a solution that you have created from the **Minimal Language** template, your experimental [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] will resemble the following example:

 ![](../modeling/media/dsl-min.png "DSL_min")

 Работа с инструментами Создайте элементы и соедините их.

 Закройте экспериментальный образец [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

> [!NOTE]
> После изменения DSL фигуры больше не будут отображаться в тестовом файле Sample. При этом возможность создавать новые элементы сохранится.

### <a name="modifying-the-template-dsl"></a>Изменение шаблона DSL
 Переименуйте и оставьте некоторые или все классы доменов и фигур в шаблоне определения DSL. Новые имена классов должны быть действительными CLR-именами без пробелов и знаков препинания.

 Рекомендуем сохранить следующие классы:

- The root class appears at the upper-left of the DSL Definition diagram, under **Classes and Relationships**. Присвойте ему другое имя, которое будет отличаться от имени DSL. For example, a DSL named **MusicLibrary** might have a root class named **Music**.

- The diagram class appears at the lower right of the DSL Definition diagram, in the **Diagram Elements** column. Возможно, чтобы его увидеть, экран придется прокрутить вправо. It is typically named _YourDsl_**Diagram**.

- If you used the **Task Flow** template and you want to create diagrams with swimlanes, keep and rename the Actor domain class and ActorSwimlane shape.

  Удалите или переименуйте другие классы в соответствии со своими потребностями.

## <a name="patterns"></a> Patterns for Defining a DSL
 Рекомендуем разрабатывать DSL путем добавления или настройки одного или двух функций за один раз. Добавьте функцию, запустите DSL и протестируйте его работу, затем добавьте еще одну или несколько функций. В число типовых функций DSL входят следующие.

- Класс домена, отношение внедрения, соединяющее элемент с моделью, фигура, предназначенная для отображения элементов класса на схеме, и средство элемента, позволяющее пользователям создавать элементы.

- Свойства домена того или иного класса и декораторы, отображающие их на схеме.

- Ссылочное отношение и соединитель, который отображает его на схеме, а также инструмент соединителя, который позволяет пользователям создавать связи.

- Настройка, требующая программного кода, например проверка ограничений или команда меню.

  В следующих разделах описывается, как построить наиболее полезные виды функций DSL. Существуют много других шаблонов, с помощью которых может быть создан DSL, но эти используются наиболее часто.

> [!NOTE]
> After adding a feature, do not forget to click **Transform All Templates** in the toolbar of Solution Explorer before you build and running your DSL.

 На следующем рисунке показаны классы и отношения, которые являются частью DSL и используются в качестве примера в данном разделе.

 ![Embedding and Reference relationships](../modeling/media/music-classes.png "Music_Classes")

 Следующий рисунок является примером модели данного DSL:

 ![Instance model of generated DSL](../modeling/media/music-instance.png "Music_Instance")

> [!NOTE]
> "Модель" означает экземпляр DSL, который создается пользователем и обычно отображается в виде схемы. В данном разделе рассматривается как схема определения DSL, так и схемы модели, которые отображаются при использовании DSL.

## <a name="classes"></a> Defining Domain Classes
 Классы доменов представляют собой концепции DSL. The instances are *model elements*. For example in a **MusicLibrary** DSL you might have Domain Classes named **Album** and **Song**.

 To create a domain class, you can drag from the **Named Domain Class** tool to the diagram, and then rename the class.

 For more information, see [Properties of Domain Classes](../modeling/properties-of-domain-classes.md).

### <a name="create-an-embedding-relationship-for-each-domain-class"></a>Создание отношения внедрения для каждого класса домена
 Каждый класс домена, кроме корневого, должен быть целевым объектом хотя бы одного отношения внедрения или наследоваться от класса, который является таким целевым объектом.

 В модели каждый элемент является узлом в едином дереве отношений внедрения. Источник и целевой объект отношения внедрения часто называют родительским и дочерним элементами.

 Выбор родительского элемента для класса домена зависит от того, как зависит время жизни этих элементов от других элементов. Если узел дерева удаляется, его поддерево обычно удаляется вместе с ним. Классы элемента, существующего независимо, встроены напрямую в корневой класс.

 Обычно если вы отображаете элемент внутри другого элемента, то показываете и его отношение к владельцу. В данном случае наиболее соответствующий родительский класс — это класс контейнера. Исключение имеет место, когда элемент внутри контейнера на самом деле является ссылкой на независимый элемент. В этом случае при удалении контейнера удаляется ссылка, но не объект, на который она указывает.

 В шаблонах определения DSL, описанных в данном разделе, будем предполагать, что элементы, отображаемые внутри контейнера, при удалении контейнера также будут удалены. Возможны и более сложные схемы, которые создаются путем определения ролей.

|Отображение элемента|Родительский класс (класс внедрения)|Пример в шаблоне решения DSL|
|------------------------------|--------------------------------|--------------------------------------|
|Фигура на схеме<br /><br /> Дорожка|Корневой класс DSL|Минимальный язык<br /><br /> Task Flow: Actor class.|
|Фигура в дорожке|Класс домена элементов, который отображаются в качестве дорожек.|Task Flow: Task class.|
|Элемент в списке в фигуре, удаляемый при удалении контейнера<br /><br /> Порт на краю фигуры|Класс домена, сопоставленный с фигурой контейнера|Class diagram: Attribute class.<br /><br /> Component diagram: Port class.|
|Элемент в списке, не удаляемый при удалении контейнера|Корневой класс DSL<br /><br /> Список с указанием связей и отношений||
|Не отображается напрямую|Класс, часть которого он формирует||

 В примере Music Library, альбомы (Album) отображаются как прямоугольники, в которых перечислены названия песен (Song). Следовательно, родителем элемента Album является корневой класс Music (Музыка), а родителем элемента Song (Песня) — класс Album (Альбом).

 To create a domain class and its embedding at the same time, click the **Embedding Relationship** tool, then click the parent class, and then click on a blank part of the diagram.

 Как правило, изменять имя отношения внедрения и его ролей не обязательно, так как они будут отслеживать имена классов автоматически.

 For more information, see [Properties of Domain Relationships](../modeling/properties-of-domain-relationships.md) and [Properties of Domain Roles](../modeling/properties-of-domain-roles.md).

> [!NOTE]
> Внедрение не является наследованием. Дочерние элементы в отношении внедрения не наследуют свойства родительских элементов.

### <a name="add-domain-properties-to-each-domain-class"></a>Добавление свойств домена в каждый класс домена
 Свойства доменов хранят значения. Examples are: Name, Title, Publication Date.

 Click **Domain Properties** in the class, press the ENTER key, and then type the name of a property. Тип свойства домена по умолчанию — строка. If you want to change the type, select the domain property, and set the **Type** in the **Properties** window. If the type that you want is not in the drop-down list, see [Adding Property Types](#addTypes).

 **Set an Element Name property.** Выберите свойство домена, которое может использоваться для определения элементов в Обозревателе языка. Например, в классе домена Song (Песня) можно выбрать свойство домена "Название". In the **Properties** window, set **Is Element Name** to `true`.

### <a name="create-derived-domain-classes"></a>Создание производных классов доменов
 Если у классов доменов должны быть экземпляры, которые наследуют его свойства и отношения, можно создать классы, которые являются производными от него. Например, класс Album (Альбом) может иметь производные классы WMA и MP3.

 Create the derived class using the **Domain Class** tool.

 Click the **Inheritance** tool, click the derived class, and then click the base class.

 Consider setting the **Inheritance Modifier** of the base class to **abstract**. Если вам могут понадобиться экземпляры базового класса, создайте для них отдельные производные классы.

 Производные классы наследуют свойства и роли базовых классов.

### <a name="tidy-the-dsl-definition-diagram"></a>Чистка схемы определения DSL
 При добавлении отношений некоторые из классов появятся сразу в нескольких местах. To reduce the number of appearances and make the diagram wider, right-click the target class of a relationship, and then click **Bring Tree Here**. For the opposite effect, right-click the target class of a relationship and click **Split Tree**. Если эти команды меню отсутствуют, убедитесь, что выбран только класс домена.

 Для перемещения классов доменов и фигур используйте сочетания клавиш CTRL + стрелка вверх и CTRL + стрелка вниз.

### <a name="test-the-domain-classes"></a>Проверка классов доменов

##### <a name="to-test-the-new-domain-classes"></a>Чтобы проверить новые классы доменов, сделайте следующее.

1. **Click Transform All Templates** in the toolbar of Solution Explorer, to generate the DSL designer code. Этот шаг можно автоматизировать. For more information, see [How to Automate Transform All Templates](https://msdn.microsoft.com/b63cfe20-fe5e-47cc-9506-59b29bca768a).

2. **Build and run the DSL.** Нажмите клавишу F5 или сочетание клавиш CTRL + F5 для запуска нового экземпляра [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] в экспериментальном режиме. В экспериментальном экземпляре [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] откройте или создайте файл с расширением вашего DSL.

3. **Open the Explorer.** At the side of the diagram is the language explorer window, which is usually named *YourLanguage* Explorer. Если вы не видите это окно, оно может быть на вкладке под Обозревателем решений. If you cannot find it, on the **View** menu, point to **Other Windows**, and then click _YourLanguage_**Explorer**.

     В обозревателе представлен вид модели в качестве дерева.

4. **Create new elements.** Right-click the root node at the top, and then click **Add New**_YourClass_.

     Новый экземпляр класса появится в Обозревателе языка.

5. При создании новых экземпляров следите за тем, чтобы все экземпляры получали разные имена. This will occur only if you have set the **Is Element Name** flag on a domain property.

6. **Examine the domain properties. With an instance of your class selected,** inspect the Properties window. Оно должно показывать свойства домена, которые вы определили для данного класса домена.

7. **Save the file, close it, and re-open it**. Все созданные экземпляры должны отобразиться в обозревателе, когда вы развернете узлы.

## <a name="shapes"></a> Defining Shapes on the Diagram
 Вы можете определить классы элементов, которые отображаются на схеме в виде прямоугольников, эллипсов или ярлыков.

#### <a name="to-define-a-class-of-elements-that-appear-as-shapes-on-a-diagram"></a>Определение класса элементов, которые отображаются на схеме в виде фигур

1. **Define and test a domain class as described in**  [Defining Domain Classes](#classes) **.**

   - Родителем класса должен быть корневой класс. Это значит, что между корневым классом и новым классом домена должно существовать отношение внедрения.

   - Если в схеме есть дорожки, то родителем может быть класс домена, сопоставленный с дорожкой. Before continuing with this procedure, see [Defining a DSL that has Swimlanes](#swimlanes).

2. **Add a shape class** to represent the elements on the model diagram. Перетащите один из следующих инструментов на схему определения DSL.

   - **Geometry Shape** provides a rectangle or ellipse.

   - **Image Shape** displays an image that you provide.

   - **Compartment Shape** is a rectangle that contains one or more lists of items.

     Переименуйте класс фигуры, который отображается в правой части схемы определения DSL под фигурами и соединителями.

3. **Define an image, if you created an image shape**.

   1. Создайте файл изображения любого размера. Поддерживаются форматы BMP, JPEG, GIF и EMF.

   2. В Обозревателе решений добавьте файл в каталог решения Dsl\Resources.

   3. Вернитесь в схему определения DSL и выберите новый класс фигуры изображения.

   4. In the Properties window, click the **Image** property.

   5. In the **Select Image** dialog box, click the drop-down menu under **File name**, and select the image.

4. **Add text decorators to the shape, to display the domain properties.**

    Чтобы отобразить имя или название элемента модели, потребуется хотя бы один декоратор.

    Right-click the header of the shape class, point to **Add**, and then click **Text Decorator**. Set the name of the decorator, and in the Properties window set its **Position**.

5. **Connect each shape with a Diagram Element Map to the domain class that it should display**.

    Click the **Diagram Element Map** tool, then click the domain class, then click the shape class.

6. **Map the properties to the text decorators.**

   1. Выберите серую линию между классом домена и классом фигуры, которая представляет карту элементов схемы.

   2. In the **DSL Details** window, click the **Decorator Maps** tab. If you do not see the **DSL Details** window, on the **View** menu, point to **Other Windows** and then click **DSL Details**. Часто нужно поднять верхнюю часть окна, чтобы увидеть все его содержимое.

   3. Выберите имя декоратора. Under **Display property**, select the name of a property of the domain class. Повторите эти шаги для каждого декоратора.

       If you want to display a property of a related element, click the drop-down tree navigator under **Path to display property**.

   4. Возле имени каждого декоратора должен быть установлен флажок.

      ![Shape Mappings and DSL Details window](../modeling/media/dsldetailswindow.png "DslDetailsWindow")

7. **Make a toolbox item for creating elements of the domain class.**

   1. In **DSL Explorer**, expand the **Editor** node and all its sub-nodes.

   2. Right-click the node under **Toolbox Tabs** that has the same name as your DSL, for example MusicLibrary. Click **Add Element Tool**.

       > [!NOTE]
       > If you right-click the **Tools** node, you will not see **Add Element Tool**. Вместо этого необходимо щелкнуть узел на уровень выше.

   3. In the Properties window with the new element tool selected, set **Class** to the domain class that you have recently added.

   4. Set **Caption** and **Tooltip**.

   5. Set **Toolbox Icon** to an icon that will appear in the toolbox. Можно выбрать новый значок или значок, который уже используется для другого инструмента.

        To create a new icon, open Dsl\Resources in **Solution Explorer**. Скопируйте и вставьте один из существующих BMP-файлов средства элемента. Переименуйте вставленную копию, а затем откройте ее двойным щелчком кнопки мыши для редактирования.

        Return to the DSL Definition diagram, select the tool, and in the Properties window click **[...]** in **Toolbox Icon**. In the **Select Bitmap** dialog box, select your .BMP file from the drop-down menu.

   For more information, see [Properties of Geometry Shapes](../modeling/properties-of-geometry-shapes.md) and [Properties of Image Shapes](../modeling/properties-of-image-shapes.md).

#### <a name="to-test-shapes"></a>Тестирование Фигур

1. **Click Transform All Templates** in the toolbar of Solution Explorer, to generate the DSL designer code.

2. **Build and run the DSL.** Нажмите клавишу F5 или сочетание клавиш CTRL + F5 для запуска нового экземпляра [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] в экспериментальном режиме. В экспериментальном экземпляре [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] откройте или создайте файл с расширением вашего DSL.

3. **Verify that the element tools appear on the toolbox.**

4. **Create shapes** by dragging from a tool onto the model diagram.

5. **Verify that each text decorator appears,** and that:

   1. You can edit it, unless you have set the **Is UI Read Only** flag on the domain property.

   2. в случае изменения свойства в окне"Свойства" или в декораторе другой вид обновляется.

   После первого тестирования фигуры можно откорректировать некоторые свойства и добавить расширенные свойства. For more information, see [Customizing and Extending a Domain-Specific Language](../modeling/customizing-and-extending-a-domain-specific-language.md).

## <a name="references"></a> Defining Reference Relationships
 Между любым классом домена источника и классом домена целевого объекта можно определить ссылочное отношение. Ссылочные отношения обычно отображаются на схеме в виде соединителей — линий между фигурами.

 Например, если музыкальные альбомы (Album) и исполнители (Artist) отображаются в схеме в виде фигур, можно определить отношение с именем ArtistsAppearedOnAlbums, связывающее исполнителей и альбомы, в которых они участвуют. См. пример на рисунке.

 ![Instance model of generated DSL](../modeling/media/music-instance.png "Music_Instance")

 Ссылочные отношения могут также связывать элементы одного типа. Например, в DSL, представляющем собой генеалогическое древо, взаимосвязь между родительскими и дочерними элементами является ссылочным отношением между персонами.

### <a name="define-a-reference-relationship"></a>Определение ссылочного отношения
 Щелкните инструмент ссылочного отношения, затем класс домена источника отношения и, наконец, целевой класс домена. Целевой класс может быть таким же как и класс источника.

 Каждое отношение имеет две роли, представленные линией с каждой стороны окна отношений. Можно выбрать каждую роль и настроить ее свойства в окне "Свойства".

 **Consider renaming the roles**. Например, в отношении между персонами можно изменить имена по умолчанию на "Родители" и "Дети", "Руководитель" и "Подчиненные", "Преподаватель" и "Студент" и т. д.

 **Adjust the multiplicities of each role**, if it is necessary. Если у каждой персоны должно быть не больше одного Руководителя, укажите для параметра кратности под ярлыком "Руководитель" в схеме значение "0..1".

 **Add domain properties to the relationship.** На рисунке отношение между исполнителем и альбомом имеет свойство роли.

 **Set the Allows Duplicates property of the relationship,** if more than one link of the same class can exist between the same pair of model elements. Например, можно разрешить Преподавателю обучать одного и того же Студента нескольким Дисциплинам.

 ![Shape maps for connectors](../modeling/media/music-connector.png "Music_Connector")

 For more information, see [Properties of Domain Relationships](../modeling/properties-of-domain-relationships.md) and [Properties of Domain Roles](../modeling/properties-of-domain-roles.md).

### <a name="define-a-connector-to-display-the-relationship"></a>Определение соединителя для отображения отношения
 Соединитель отображает линию между двумя фигурами в схеме модели.

 Drag the **Connector** tool onto the DSL definition diagram.

 Добавьте текстовые декораторы если необходимо отобразить ярлыки на соединителе. Установите их расположение. To let the user move a text decorator, set its **Is Moveable** property.

 Use the **Diagram Element Map** tool to link the connector to the reference relationship.

 With the diagram element map selected, open the **DSL Details** window, and open the **Decorator Maps** tab.

 Select each **Decorator** and set **Display property** to the correct domain property.

 Make sure that a check mark appears next to each item in the **Decorators** list.

### <a name="define-a-connection-builder-tool"></a>Определение средства построителя подключений
 In the **DSL Explorer** window, expand the **Editor** node and all its subnodes.

 Right-click the node that has the same name as your DSL, and then click **Add New Connection Tool**.

 Выбрав новый инструмент, в окне "Свойства":

- Set the **Caption** and **Tooltip**.

- Click **Connection Builder** and select the appropriate builder for the new relationship.

- Set **Toolbox Icon** to the icon that you want to appear in the toolbox. Можно выбрать новый значок или значок, который уже используется для другого инструмента.

     To create a new icon, open Dsl\Resources in **Solution Explorer**. Скопируйте и вставьте один из существующих BMP-файлов средства элемента. Переименуйте вставленную копию, а затем откройте ее двойным щелчком кнопки мыши для редактирования.

     Return to the DSL Definition diagram, select the tool, and in the Properties window click **[...]** in **Toolbox Icon**. In the **Select Bitmap** dialog box, select your .BMP file from the drop-down menu.

##### <a name="to-test-a-reference-relationship-and-connector"></a>Тестирование ссылочного отношения и соединителя

1. **Click Transform All Templates** in the toolbar of Solution Explorer, to generate the DSL designer code.

2. **Build and run the DSL.** Нажмите клавишу F5 или сочетание клавиш CTRL + F5 для запуска нового экземпляра [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] в экспериментальном режиме. В экспериментальном экземпляре [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] откройте или создайте файл с расширением вашего DSL.

3. **Verify that the connection tool appears on the toolbox.**

4. **Create shapes** by dragging from a tool onto the model diagram.

5. **Create connections** between the shapes. Выберите соединитель, щелкните фигуру, а затем выберите другую фигуру.

6. **Verify that you cannot create connections between inappropriate classes.** Например, если установлено отношение между Альбомами и Исполнителями, убедитесь, что нельзя связать Исполнителей с Исполнителями.

7. **Verify that the multiplicities are correct. For example, verify that you cannot connect a Person to more than one manager.**

8. **Verify that each text decorator appears,** and that:

   1. You can edit it, unless you have set the **Is UI Read Only** flag on the domain property.

   2. в случае изменения свойства в окне"Свойства" или в декораторе другой вид обновляется.

   После первого тестирования соединителя можно откорректировать некоторые свойства и добавить расширенные свойства. For more information, see [Customizing and Extending a Domain-Specific Language](../modeling/customizing-and-extending-a-domain-specific-language.md).

## <a name="compartments"></a> Defining Shapes that Contain Lists: Compartment Shapes
 Фигура секции содержит один или несколько списков элементов. Например, в DSL Music Library можно использовать фигуру секции для представления музыкальных Альбомов. В каждом Альбоме есть список Песен.

 ![Compartment Shape](../modeling/media/compartmentshape.png "CompartmentShape")

 Самый простой способ добиться этого эффекта в определении DSL — это определить один класс домена для контейнера и один класс домена для каждого списка. Класс контейнера сопоставлен с фигурой секции.

 ![Shape map](../modeling/media/music-mapcomp.png "Music_MapComp")

 For more information, see [Properties of Compartment Shapes](../modeling/properties-of-compartment-shapes.md).

#### <a name="to-define-a-compartment-shape"></a>Определение фигуры секции

1. **Create the container domain class**. Click the **Embedding Relationship** tool, click the root class of the model, and then click a blank part of the DSL definition diagram. Это создаст класс домена, который на рисунке примера называется Album.

     В качестве альтернативы вместо встраивания в корневой класс можно встроить контейнер в класс домена, сопоставленный с дорожкой.

     Add a domain property such as Name to the class, and set its **Is Element Name** flag in the Properties window.

2. **Create the list item domain class**. Click the **Embedding Relationship** tool, click the container class (Album) and then click a blank part of the diagram. Это создаст класс домена, который на рисунке примера называется Song (Песня).

     Add a domain property such as Title to the class, and set its **Is Element Name** flag.

     Добавьте другие свойства домена.

     Добавьте по классу домена для каждого списка элементов, который необходимо отобразить.

3. **To mix several types of item in the list**, create classes that inherit from the list class. Make the list class abstract by setting its **Inheritance Modifier**.

     Например, если вы хотите, чтобы классическая музыка сортировалась по композитору, а не по исполнителю, можно создать в классе Song (Песня) два подкласса: ClassicalSong (Классические) и NonClassicalSong (Не классические).

4. **Create the compartment shape**. Drag from the **Compartment Shape** tool onto the DSL definition diagram.

     Добавьте текстовый декоратор и укажите для него имя.

     Добавьте секцию и укажите для нее имя.

5. To let the user hide the list compartments, right-click the compartment shape class, point to **Add**, and then click **Expand/Collapse Decorator**. В окне "Свойства" задайте расположение декоратора.

6. Click the **Diagram Element Map** tool, click the container domain class, and then click the compartment shape.

7. Выберите связь карты элемента схемы между классом домена и фигурой. In the **DSL Details** window:

    1. Click the **Decorators** tab. Click the name of the decorator and then select the appropriate item under **Display Property**. Убедитесь, что возле имени каждого декоратора установлен флажок.

    2. Click the **Compartment Maps** tab.

         Выберите имя секции.

         Under **Displayed elements collection path**, navigate to the list element class (Song). Щелкните стрелку раскрывающегося меню, чтобы воспользоваться инструментом навигации.

         Under **Display Property**, select the property that should be displayed in the list. В этом примере это свойство — Название.

> [!NOTE]
> Используя поля "Путь" в карте декораторов и полях в карте секций, установите более сложные отношения между классами доменов и фигурой секции.

#### <a name="to-define-a-tool-for-creating-the-shape"></a>Определение инструмента для создания фигуры

1. **Make a toolbox item for creating elements of the domain class.**

2. In **DSL Explorer**, expand the **Editor** node and all its sub-nodes.

3. Right-click the node under **Toolbox Tabs** that has the same name as your DSL, for example MusicLibrary. Click **Add Element Tool**.

    > [!NOTE]
    > If you right-click the **Tools** node, you will not see **Add Element Tool**. Вместо этого необходимо щелкнуть узел на уровень выше.

4. In the Properties window with the new element tool selected, set **Class** to the domain class that you have recently added.

5. Set **Caption** and **Tooltip**.

6. Set **Toolbox Icon** to an icon that will appear in the toolbox. Можно выбрать новый значок или значок, который уже используется для другого инструмента.

     To create a new icon, open Dsl\Resources in **Solution Explorer**. Скопируйте и вставьте один из существующих BMP-файлов средства элемента. Переименуйте вставленную копию, а затем откройте ее двойным щелчком кнопки мыши для редактирования.

     Return to the DSL Definition diagram, select the tool, and in the Properties window click **[...]** in **Toolbox Icon**. In the **Select Bitmap** dialog box, select your BMP file from the drop-down menu.

#### <a name="to-test-a-compartment-shape"></a>Тестирование фигуры сегмента

1. **Click Transform All Templates** in the toolbar of Solution Explorer, to generate the DSL designer code.

2. **Build and run the DSL.** Нажмите клавишу F5 или сочетание клавиш CTRL + F5 для запуска нового экземпляра [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] в экспериментальном режиме. В экспериментальном экземпляре [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] откройте или создайте файл с расширением вашего DSL.

3. **Verify that the tool appears on the toolbox.**

4. Перетащите инструмент в схему модели. Будет создана новая фигура.

    Убедитесь, что имя элемента отображается и автоматически получает значение по умолчанию.

5. Right-click the header of the new shape, and then click Add *Your List Item.* В этом примере используется команда "Добавить песню".

    Убедитесь, что элемент отображается в списке под новым именем.

6. Щелкните один из элементов списка и проверьте окно "Свойства". В нем должны появиться свойства элементов списка.

7. Откройте Обозреватель языка. Убедитесь, что узлы контейнера содержат узлы элементов списка.

   ![Generated explorer of DSL](../modeling/media/music-explorer.png "Music_Explorer")

   После первого тестирования фигуры секции можно откорректировать некоторые свойства и добавить расширенные свойства. For more information, see [Customizing and Extending a Domain-Specific Language](../modeling/customizing-and-extending-a-domain-specific-language.md).

### <a name="displaying-a-reference-link-in-a-compartment"></a>Отображение ссылочной связи в секции
 Обычно элемент, который отображается в секции, является дочерним для элемента, который представлен фигурой фрагмента. Однако в некоторых случаях можно отобразить элемент, который связан с ним ссылочным отношением.

 Например, можно добавить вторую секцию в элемент AlbumShape, отображающий список Исполнителей, которые связаны с Альбомом.

 В этом случае секция должна отображать связь вместо элемента, на который она ссылается. Это связано с тем, что, когда пользователь выбирает элемент в секции и нажимает клавишу DELETE, должна удаляться связь, а не элемент, на который создана ссылка.

 Тем не менее можно сделать так, чтобы имя элемента, на который создана ссылка, отображалось в секции.

 Следующая процедура предполагает, что вы уже создали класс домена, ссылочное отношение, фигуру секции и карту элементов схемы, как описано выше в этом разделе.

##### <a name="to-display-a-reference-link-in-a-compartment"></a>Отображение ссылочной связи в секции

1. **Add a compartment to the compartment shape**. On the DSL Definition diagram, right-click the compartment shape class, point to **Add**, and then click **Compartment**.

2. Set **Displayed elements collection path** to navigate to the link, instead of its target element. Откройте раскрывающееся меню и выберите в представлении дерева вместо цели ссылочное отношение. In the example, the relationship is **ArtistAppearedOnAlbums**.

3. Set **Path to Display Property** to navigate from the link to the target element. In the example, this is **Artist**.

4. Set **Display Property** to the appropriate property of the target element, for example **Name**.

5. **Transform All Templates**, build and run the DSL, and open a test model.

6. В схеме модели создайте соответствующие классы фигур, присвойте им имена и создайте связь между ними. В фигуре секции должны появиться имена связанных элементов.

7. Выберите связь или элемент в фигуре секции. Связь и элемент должны исчезнуть.

## <a name="ports"></a> Defining Ports on the Boundary of another Shape
 Порт — это фигура, которая находится на границе с другой фигурой.

 Порты могут также использоваться для предоставления фиксированной точки соединения с другой фигурой, для которой пользователь может нарисовать соединители. В данном случае фигуру порта можно сделать прозрачной.

 To see an example that uses ports, select the **Component Diagram** template when you create a new DSL solution. В данном примере показаны основные точки, которые можно использовать при определении портов.

- Класс домена, который представляет контейнер портов (`Component`).

- Класс домена, который представляет порты. В этом примере используется класс `ComponentPort`.

- Отношение внедрения между классом домена контейнера и классом домена порта. For more information, see [Defining Domain Classes](#classes).

- Если в одном контейнере нужно смешать разные типы портов, можно создать подклассы класса домена порта. В данном примере `InPort` и `OutPort` наследуются от `ComponentPort`.

- Класс домена контейнера может быть сопоставлен с любым видом фигуры. В этом примере используется `ComponentShape`. For more information, see [Defining Shapes](#shapes).

- Классы доменов портов сопоставлены с фигурами портов. Можно сопоставить либо производные классы с отдельными классами фигур портов, либо базовый класс с одним классом фигуры порта.

  In other respects, port shapes behave as described in [Defining Shapes](#shapes).

  For more information, see [Properties of Port Shapes](../modeling/properties-of-port-shapes.md).

## <a name="swimlanes"></a> Defining a DSL that has Swimlanes
 Дорожки — это вертикальные или горизонтальные разделения схемы. Каждая дорожка соответствует элементу модели. Определение DSL требует одного класса домена для элементов дорожек.

 Лучший способ создать DSL с дорожками — это создать новое решение DSL и выбрать шаблон решения "Поток задач". В определении DSL класс субъекта является классом домена, сопоставленным с дорожкой. Переименуйте его и другие классы в соответствии со своим проектом.

 Чтобы добавить класс, который будет отображаться как фигура внутри дорожки, создайте отношение внедрения между классом дорожки и новым классом. Пользователи смогут перетаскивать элементы из одной дорожки в другую, но каждый элемент всегда будет находиться внутри конкретной дорожки. В шаблоне решения "Поток задач", FlowElement является дочерним классом класса дорожки.

 Чтобы добавить класс, который будет отображаться как фигура, независимая от дорожки, создайте отношение внедрения между корневым и новым классами. Пользователи смогут размещать эти фигуры в любом месте схемы, в т. ч. на границах и за пределами дорожек. В шаблоне решения "Поток задач", Comment является дочерним классом класса дорожки.

 For more information, see [Properties of Swimlanes](../modeling/properties-of-swimlanes.md).

## <a name="addTypes"></a> Adding Property Types

### <a name="domain-enumerations-and-literals"></a>Доменные перечисления и литералы
 Доменное перечисление — это тип с несколькими значениями литералов.

 To add a domain enumeration, right-click the root of the model in the **DSL Explorer** and then click **Add New Domain Enumeration**. The element will appear in the **DSL Explorer** under the **Domain Types** node. Этот элемент не отображается в схеме.

 To add enumeration literals to the domain enumeration, right-click the domain enumeration in the **DSL Explorer** and then click **Add New Enumeration Literal**.

 По умолчанию свойство, которое имеет тип перечисления, может иметь только одно значение перечисления за раз. If you want users and programmers to be able to set any combination of values - a "bit field" - set the **IsFlags** property of the Enumeration.

### <a name="external-types"></a>Внешние типы
 When you set the type of a domain property, if you do not find the type you want in the **Type** drop-down list, you can add an external type. For example, you could add the **System.Drawing.Color** type to the list.

 To add a type, right-click the root of the model in DSL Explorer, and then click **Add New External Type**. In the Properties window, set the name to **Color** and the namespace to **System.Drawing**. This type now appears in DSL Explorer under **Domain Types**. и будет доступен для выборе при установке типа свойства домена.

## <a name="custom"></a> Customizing the DSL
 Используя техники, описанные в этом разделе, можно быстро создать DSL со схематическим представлением, читаемой формой XML и основными инструментами, необходимыми для генерирования кода или других артефактов.

 Существуют два метода расширения определения DSL.

1. Точная настройка DSL с использованием многочисленных функций определения DSL. Например, можно сделать единое средство подключения, способное создавать несколько типов соединителей, и настроить правила, по которым удаление одного элемента ведет к удалению связанных элементов. Большинство этих техник требуют установки значений в определении DSL, а некоторые — написания нескольких строк программного кода.

     For more information, see [Customizing and Extending a Domain-Specific Language](../modeling/customizing-and-extending-a-domain-specific-language.md).

2. Расширение инструментов моделирования с помощью программного кода для достижения более сложных эффектов. Например, можно создать команды меню, способные изменять модель, а также инструменты, соединяющие в себе два и более DSL. VMSDK разработан специально для того, чтобы облегчить интеграцию расширений с кодом, который генерируется из определения DSL.  For more information, see [Writing Code to Customise a Domain-Specific Language](../modeling/writing-code-to-customise-a-domain-specific-language.md).

### <a name="changing-the-dsl-definition"></a>Изменение определения DSL
 При создании любого элемента в определении DSL многие значения устанавливаются автоматически. Установленные значения можно изменять. Это упрощает разработку DSL и в то же время позволяет осуществлять значительные настройки.

 Например, когда фигура сопоставляется с элементом, путь родительского элемента сопоставления автоматически устанавливается согласно отношению внедрения соответствующего класса домена. Если же впоследствии отношение внедрения корректируется, путь родительского элемента автоматически не изменяется.

 Следовательно, необходимо знать, что при изменении некоторых взаимосвязей в определении DSL нет ничего необычного в том, что при сохранении определения или трансформации всех шаблонов будут выдаваться сообщения об ошибках. Большинство этих ошибок легко исправить. Откройте сообщение об ошибке двойным щелчком кнопки мыши, чтобы найти расположение ошибки.

 See also [How to: Change the Namespace of a Domain-Specific Language](../modeling/how-to-change-the-namespace-of-a-domain-specific-language.md).

## <a name="trouble"></a> Troubleshooting
 В следующей таблице перечислено большинство стандартных проблем, возникающих при разработке DSL, а также предложения по их решению. More advice is available on the [Visualization Tools Extensibililty Forum](https://go.microsoft.com/fwlink/?LinkId=186074).

|Проблема|Предложение|
|-------------|----------------|
|Изменения, внесенные в файл определения DSL, не работают.|Click **Transform All Templates** in the toolbar above Solution Explorer, and then rebuild the solution.|
|Фигуры показывают имя декоратора вместо значения свойства.|Настройте сопоставление декоратора. В схеме определения DSL щелкните карту элементов схемы — это серая линия между классом домена и классом фигуры.<br /><br /> Open the **DSL Details** window. If you cannot see it, on the View menu, point to **Other Windows**, and then click **DSL Details**.<br /><br /> Click the **Decorator Maps** tab. Select the name of the decorator. Убедитесь, что флажок рядом с ним установлен. Under **Display property**, select the name of a domain property.<br /><br /> For more information, see [Shapes on the Diagram](#shapes).|
|В Обозревателе DSL не удается добавить коллекцию. Например, при щелчке правой кнопкой мыши по пункт "Инструменты" в меню не отображается команда "Добавить инструмент".<br /><br /> В Обозревателе DSL не удается добавить элемент в список.|Щелкните элемент над интересующим вас узлом правой кнопкой мыши. Если вы хотите добавить элемент в список, ищите команду "Добавить" не в узле списка, а во владельце.|
|Я создал класс домена, но не могу создать экземпляры в Обозревателе языка.|Каждый класс домена, кроме корневого, должен быть целевым объектом отношения внедрения.|
|В Обозревателе DSL элементы отображаются только с именами их типов.|In the DSL Definition, select a domain property of the class and in the Properties window, set **Is Element Name** to true.|
|DSL всегда открывается в XML-редакторе.|Это происходит из-за ошибки чтения файла. Даже если вы исправите эту ошибку, необходимо будет специально сбросить редактор, чтобы он больше не выступал в качестве конструктора DSL.<br /><br /> Right-click the project item, click **Open With** and select _YourLanguage_**Designer (Default)** .|
|Панель элементов в DSL не отображается после изменения имен сборки.|Inspect and update **DslPackage\GeneratedCode\Package.tt** For more information, see [How to: Change the Namespace of a Domain-Specific Language](../modeling/how-to-change-the-namespace-of-a-domain-specific-language.md).|
|Панель элементов в DSL не отображается, хотя имя сборки не изменялось.<br /><br /> Либо появляется сообщение о невозможности загрузить расширение.|Сбросьте экспериментальный экземпляр и выполните сборку решения заново.<br /><br /> 1.  At the Windows Start menu, under **All Programs**, expand [!INCLUDE[vssdk_current_long](../includes/vssdk-current-long-md.md)], then **Tools**, and then click **Reset the Microsoft Visual Studio Experimental Instance**.<br />2.  On the [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]**Build** menu, click **Rebuild Solution**.|

## <a name="see-also"></a>См. также раздел
 [Getting Started with Domain-Specific Languages](../modeling/getting-started-with-domain-specific-languages.md) [Creating a Windows Forms-Based Domain-Specific Language](../modeling/creating-a-windows-forms-based-domain-specific-language.md) [Creating a WPF-Based Domain-Specific Language](../modeling/creating-a-wpf-based-domain-specific-language.md)
