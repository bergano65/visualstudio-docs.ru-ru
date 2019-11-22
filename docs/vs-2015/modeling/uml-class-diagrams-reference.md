---
title: 'UML Class Diagrams: Reference | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.common.generalization.properties
- vs.teamarch.logicalclassdiagram.toolbox
- vs.teamarch.UMLModelExplorer.association
- vs.teamarch.common.unspecifiedtype.properties
- vs.teamarch.logicalclassdiagram.diagram
- vs.teamarch.UMLModelExplorer.logicalclassdiagram
- vs.teamarch.UMLModelExplorer.generalization
- vs.teamarch.common.unspecifiedtype
helpviewer_keywords:
- UML diagrams, class
- diagrams - modeling, class
- UML, class diagrams
- class diagrams - UML
- diagrams - modeling, UML class
ms.assetid: b7c88be0-0d86-4d65-af74-f37e8812d20f
caps.latest.revision: 43
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: da4e0e3bab904b660f3d843e105b7d256a63a1b5
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297227"
---
# <a name="uml-class-diagrams-reference"></a>UML-схемы классов: справочные материалы
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Схема классов UML описывает структуры объектов и информации, используемые приложением как для внутренних задач, так и в рамках взаимодействия с пользователями. Она описывает информацию без ссылки на какую-либо конкретную реализацию. Ее классы и отношения можно реализовать различными способами, например в виде таблиц базы данных, XML-узлов или композиций программных объектов.

> [!NOTE]
> Этот раздел посвящен UML-схемам классов. Существует другой вид схемы классов  схема классов .NET, которая используется для визуализации программного кода. For more information, see [Designing and Viewing Classes and Types](https://go.microsoft.com/fwlink/?LinkId=142231).

 To create a UML class diagram, on the **Architecture** menu, choose **New UML or Layer Diagram**. For more information about how to draw UML class diagrams, see [UML Class Diagrams: Guidelines](../modeling/uml-class-diagrams-guidelines.md). For more information about how to create and draw modeling diagrams, see [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md).

 Чтобы узнать, какие версии Visual Studio поддерживают эту функцию, см. раздел [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="reading-class-diagrams"></a>Чтение схем классов
 В таблице в этом разделе описаны элементы, которые можно увидеть на схеме классов UML. Сведения о свойствах этих элементов см. в следующих разделах:

- [Свойства типов на схемах классов UML](../modeling/properties-of-types-on-uml-class-diagrams.md)

- [Свойства атрибутов на схемах классов UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md)

- [Свойства операций на схемах классов UML](../modeling/properties-of-operations-on-uml-class-diagrams.md)

- [Свойства ассоциаций на схемах классов UML](../modeling/properties-of-associations-on-uml-class-diagrams.md)

  ![Three classes showing relationships and properties](../modeling/media/uml-classovreading.png "UML_ClassOvReading")

| **Shape** |       **Элемент**        |                                                                                                                                                             **Описание**                                                                                                                                                              |
|-----------|--------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     1     |        **Класс**         |                                                           Определение объектов, совместно обладающих заданными характеристиками структуры или поведения. For more information, see [Properties of types on UML class diagrams](../modeling/properties-of-types-on-uml-class-diagrams.md).                                                            |
|     1     |        Классификатор        |                                                                                                             Общее имя для класса, интерфейса или перечисления. Компоненты, варианты использования и субъекты также являются классификаторами.                                                                                                             |
|     2     | Элемент управления "Свернуть/развернуть" |                                                                                         Если сведения о классификаторе не отображаются, щелкните элемент развертывания в верхней левой части классификатора. Может также потребоваться щелкнуть элемент [+] для каждого сегмента.                                                                                         |
|     3     |      **Attribute (XElement Dynamic Property)** (Attribute (динамическое свойство XElement))       |   Типизированное значение, прикрепленное к каждому экземпляру классификатора.<br /><br /> To add an attribute, click the **Attributes** section and then press **ENTER**. Введите сигнатуру атрибута. For more information, see [Properties of attributes on UML class diagrams](../modeling/properties-of-attributes-on-uml-class-diagrams.md).   |
|     4     |      **Operation**       | Метод или функция, которые могут выполняться экземплярами классификатора. To add an operation, click the **Operations** section and then press **ENTER**. Введите сигнатуру операции. For more information, see [Properties of operations on UML class diagrams](../modeling/properties-of-operations-on-uml-class-diagrams.md). |
|     5     |     **Association**      |                                                                  Отношение между членами двух классификаторов. For more information, see [Properties of associations on UML class diagrams](../modeling/properties-of-associations-on-uml-class-diagrams.md).                                                                   |
|    5а     |     **Статистическая обработка**      |                                                                                                    Ассоциация, представляющая отношение совместного владения. The **Aggregation** property of the owner role is set to **Shared**.                                                                                                     |
|    5б     |     **Composition**      |                                                                                                      Ассоциация, представляющая отношение целого и части. The **Aggregation** property of the owner role is set to **Composite**.                                                                                                      |
|     6     |   **Association Name**   |                                                                                                                                         Имя ассоциации. Имя можно оставить пустым.                                                                                                                                          |
|     7     |      **Role Name**       |                       Имя роли, представляющей один конец ассоциации. Может использоваться для ссылки на связанный объект. В предыдущем примере для любого заказа `O``O.ChosenMenu` является связанным меню.<br /><br /> Каждая роль имеет свои собственные свойства, перечисленные в свойствах ассоциации.                       |
|     8     |     **Multiplicity**     |                                         Указывает, сколько объектов на этом конце могут быть связаны с каждым объектом на другом конце. В примере каждый заказ должен быть связан только с одним меню.<br /><br /> **\\** \* means that there is no upper limit to the number of links that can be made.                                         |
|     9     |    **Generalization**    |  The *specific* classifier inherits part of its definition from the *general* classifier. Общий классификатор находится на той стороне соединителя, где изображен наконечник стрелки. Атрибуты, ассоциации и операции наследуются специальным классификатором.<br /><br /> Use the **Inheritance** tool to create a generalization between two classifiers.   |

 ![Package containing interface and enumeration](../modeling/media/uml-classovpackage.png "UML_ClassOvPackage")

|Фигура|Элемент|Описание|
|-----------|-------------|-----------------|
|10|**Interface**|Определение части наблюдаемого извне поведения объекта. For more information, see [Properties of types on UML class diagrams](../modeling/properties-of-types-on-uml-class-diagrams.md).|
|11|**Enumeration**|Классификатор, состоящий из набора значений литералов.|
|12|**Пакет**|Группа классификаторов, ассоциаций, действий, жизненных циклов, компонентов и пакетов. Логическая схема классов показывает, что классификаторы членов и пакеты содержатся в пакете.<br /><br /> Names are scoped within packages so that **Class1** within **Package1** is distinct from **Class1** outside that package. The name of the package appears as part of the **Qualified Name** properties of its contents.<br /><br /> You can set the **Linked Package** property of any UML diagram to refer to a package. После этого все элементы, создаваемые на этой схеме, становятся частью этого пакета. They will appear under the package in **UML Model Explorer**.|
|13|**Import**|Отношение между пакетами, указывающее на то, что один пакет включает в себя все определения другого.|
|14|**Dependency**|Определение или реализация зависимого классификатора может измениться, если изменяется классификатор, на который указывает стрелка.|

 ![Realization shown with conector and lollipop](../modeling/media/uml-classovrealize.png "UML_ClassOvRealize")

|Фигура|**Элемент**|Описание|
|-----------|-----------------|-----------------|
|15|**Realization**|Класс реализует операции и атрибуты, определенные интерфейсом.<br /><br /> Use the **Inheritance** tool to create a realization between a class and an interface.|
|16|**Realization**|Альтернативное представление того же самого отношения. Метка на символе, представляющем собой круг на вертикальной линии, определяет интерфейс.<br /><br /> Чтобы создать это представление, выберите существующее отношение реализации. Рядом с ассоциацией отображается тег действия. Click the action tag, and then click **Show as Lollipop**.|

## <a name="see-also"></a>См. также раздел
 [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md) [UML Class Diagrams: Guidelines](../modeling/uml-class-diagrams-guidelines.md) [Properties of types on UML class diagrams](../modeling/properties-of-types-on-uml-class-diagrams.md) [Properties of attributes on UML class diagrams](../modeling/properties-of-attributes-on-uml-class-diagrams.md) [Properties of operations on UML class diagrams](../modeling/properties-of-operations-on-uml-class-diagrams.md) [Properties of associations on UML class diagrams](../modeling/properties-of-associations-on-uml-class-diagrams.md)
